# R-002 Extended — Per-cron model preset selection with three job types

## Summary
Implement per-cron model preset selection supporting three job types:
1. **Contexted AI** (current behavior): Uses parent session's model preset
2. **Contextless AI**: Creates new session with specified model preset
3. **Shell**: AIless task that executes commands directly

## Design Decisions

### CronPayload model_preset semantics
- `model_preset: str | None = "__parent__"` in `CronPayload`
- Default `"__parent__"` maintains backward compatibility (no migration needed)
- Three values:
  - `"__parent__"` → Contexted AI (use parent session's model preset)
  - `None` → Shell task (AIless, execute command)
  - Any preset name → Contextless AI (create new session with that preset)

### WebUI model preset dropdown
- Three options: "As parent", "No model", then preset names
- "As parent" = `"__parent__"`
- "No model" = `None`
- Preset names = actual preset names

### Execution flow
1. **Contexted AI** (`"__parent__"`): Current behavior - run in parent session
2. **Contextless AI** (preset name):
   - Create new session with that preset
   - Run task
   - Join outcome to parent session (smart consolidation, avoid sending full context)
3. **Shell** (`None`):
   - Execute command directly
   - Attach output to parent session
   - Return error code on failure

## Requirements Covered
- **R-002** — Per-cron model preset selection (parent of this extended plan)
- **R-002.1** — Contextless AI cron jobs (Q17, Q21, Q22)
- **R-002.2** — Pure shell cron jobs (Q18, Q22, Q25)
- **R-003** — Superseded by R-002.2

## Implementation Plan

### Phase 1: Core Changes (Week 1-2)

#### A. Update CronPayload type (`nanobot/cron/types.py`)
- Add `PARENT_MODEL_PRESET = "__parent__"` constant
- Add `model_preset: str | None = PARENT_MODEL_PRESET` field
- Update `from_store_dict` to handle new field
- Update `_write_store` in `CronService` to serialize model_preset

#### B. Update CronJob execution (`nanobot/cron/bound_runner.py`)
- Read `model_preset` from `job.payload`
- Implement three execution paths:
  - Contexted AI: current `run_bound_cron_job` logic
  - Contextless AI: new `run_contextless_cron_job` method
  - Shell: new `run_shell_cron_job` method
- Implement smart outcome joining for contextless AI (Q17)

#### C. Update session creation for contextless AI (`nanobot/agent/loop.py`)
- Extend `set_session_model_preset` to accept optional `model_preset` parameter
- Add method to create new session with specified preset
- Implement outcome joining mechanism

### Phase 2: WebUI Integration (Week 3)

#### A. Update WebUI types (`webui/src/lib/types.ts`)
- Add `model_preset: string | null = "__parent__"` to `SessionAutomationJob.payload`
- Update `AutomationUpdatePayload` to include `model_preset`

#### B. Update WebUI API (`webui/src/lib/api.ts`)
- Add model_preset field to automation update payloads
- Update API endpoints to handle model_preset

#### C. Update WebUI components
- Add model preset dropdown to automation editor
- Implement three-option dropdown: "As parent", "No model", then presets
- Add validation for model preset selection

### Phase 3: Testing (Week 4)

#### A. Unit tests
- Test CronPayload serialization with model_preset
- Test three execution paths (contexted, contextless, shell)
- Test model preset validation
- Test session creation for contextless AI

#### B. Integration tests
- Test cron job execution with each model_preset value
- Test outcome joining for contextless AI
- Test shell task execution
- Test WebUI automation editor with model_preset

#### C. End-to-end tests
- Test full workflow: create cron job with each model_preset → execute → verify
- Test backward compatibility (existing jobs without model_preset field)

### Phase 4: Verification (Week 5)
- Run all tests
- Verify acceptance criteria
- Fix any issues

## Acceptance Criteria

### Core Functionality
- [ ] Cron job definition can reference a model preset by name
- [ ] Contexted AI jobs use parent session's model preset (current behavior)
- [ ] Contextless AI jobs create new session with specified preset
- [ ] Shell jobs execute commands directly without AI
- [ ] Outcome joining works for contextless AI (smart consolidation: prompt injection or parent session consolidates child findings)
- [ ] Outcome joining mechanism supports both append-to-history (A) and child-session (C) modes; user-pickable
- [ ] Error handling differs by job type: Contexted AI runs on parent's model preset; Contextless can return error; Shell returns failure error and error code
- [ ] Asynchronous execution; check current implementation and support current behaviour

### WebUI
- [ ] WebUI and TUI show model preset field when editing a cron job
- [ ] Model preset dropdown has three options: "As parent", "No model", then presets
- [ ] Model preset validation works
- [ ] Existing cron jobs continue to work without modification

### Testing
- [ ] Unit tests for CronPayload with model_preset
- [ ] Integration tests for three execution paths
- [ ] WebUI tests for automation editor with model_preset
- [ ] End-to-end tests for full workflow

## Backward Compatibility

### Existing Jobs
- Jobs without `model_preset` field default to `"__parent__"` (contexted AI)
- No migration needed - existing jobs continue to work
- Current behavior preserved for all existing cron jobs

### New Jobs
- Can explicitly set `model_preset` to `"__parent__"`, `None`, or a preset name
- WebUI provides clear options for users

## Dependencies

### Required
- Model preset catalog must be available during cron job execution
- Session manager must support model preset metadata
- Runtime resolver must support preset selection

### Optional
- Model preset validation can be deferred to runtime
- Invalid model preset can fall back to session default

## Risk Mitigation

### Model preset validation
- Validate model preset exists before job execution
- Fall back to session default if model preset is invalid
- Log warnings for invalid model preset references

### Session binding
- Ensure model preset is set before session is used
- Handle race conditions between model preset setting and job execution
- Ensure model preset is persisted with session metadata

### Performance
- Model preset validation should be cached
- Session model preset setting should be efficient
- No performance impact on existing cron jobs

## Implementation Steps

### Step 1: Update CronPayload
1. Add `PARENT_MODEL_PRESET = "__parent__"` constant
2. Add `model_preset: str | None = PARENT_MODEL_PRESET` field
3. Update `from_store_dict` method
4. Update serialization in `_write_store`

### Step 2: Update CronJob execution
1. Modify `run_bound_cron_job` to read model_preset
2. Implement `run_contextless_cron_job` method
3. Implement `run_shell_cron_job` method
4. Implement smart outcome joining for contextless AI

### Step 3: Update session creation
1. Extend `set_session_model_preset` to accept optional model_preset
2. Add method to create new session with specified preset
3. Implement outcome joining mechanism

### Step 4: Update WebUI
1. Add model_preset to SessionAutomationJob
2. Update AutomationUpdatePayload
3. Update API endpoints
4. Update WebUI components

### Step 5: Testing
1. Write unit tests
2. Write integration tests
3. Write end-to-end tests
4. Run all tests

### Step 6: Verification
1. Verify acceptance criteria
2. Fix any issues
3. Deploy changes

## Decisions (final, from lani session Q11–Q30)

- Q11: The three-job-type design is an **extension** to R-002, not a replacement.
- Q15: The design is a **precursor**; the model is the same as the session model.
- Q16: Use the existing parent-session design if it has a parent session; extend it.
- Q17: Smart outcome joining: do not send the whole context to a different model. Options: prompt injection, or trigger the parent session to consolidate the findings of the child session.
- Q18: Shell task should have something to attach the output to (the "parent" session), but in reality it does not need a session.
- Q19: Outcome joining mechanism is **A or C** (append to existing session history, or create a child session); user-pickable option.
- Q20: No migration needed; one of the new types should be the same as the current implementation.
- Q21: Prefer separate methods over parameter-bloated existing methods.
- Q22: Contexted AI runs on the parent's model preset; Contextless can return error; Shell returns the failure error and error code.
- Q23: Full coverage required.
- Q24: Timeline does not matter.
- Q25: `model_preset: None` means AIless task.
- Q26: Yes.
- Q27: Should be asynchronous; check how it is implemented currently and support current behaviour.
- Q28: WebUI list: "As parent", "No model", then preset names. "As parent" = Contexted; `None` = Shell; different preset = Contextless.
- Q29: Design is model-based.
- Q30: Keep the requirement as the business/usage requirement; add smaller implementational requirements R-002.1, R-002.2, etc.

## Open Questions

### Q17 (resolved): Smart outcome joining
- How to implement smart consolidation without sending full context?
- Should parent session be triggered to consolidate findings?
- What's the optimal prompt injection strategy?

### Q18 (resolved): Shell task output attachment
- How to attach shell output to parent session?
- What format should the output take?
- How to handle shell errors?

### Q28 (resolved): WebUI dropdown implementation
- How to implement the three-option dropdown?
- How to handle the "As parent" vs "No model" distinction?
- How to populate preset names in the dropdown?

### Q29 (resolved): Model-based design
- How to ensure the design is truly model-based?
- How to handle model preset validation?
- How to ensure consistency across all three job types?

## Timeline

### Phase 1: Core Implementation (Week 1-2)
- Update CronPayload type
- Update CronJob execution
- Update session creation

### Phase 2: WebUI Integration (Week 3)
- Update WebUI types
- Update WebUI API
- Update WebUI components

### Phase 3: Testing (Week 4)
- Write unit tests
- Write integration tests
- Write end-to-end tests

### Phase 4: Verification (Week 5)
- Run all tests
- Verify acceptance criteria
- Fix any issues

## Dependencies

### Internal
- `nanobot/cron/types.py`
- `nanobot/cron/service.py`
- `nanobot/cron/bound_runner.py`
- `nanobot/agent/loop.py`
- `nanobot/session/model_selection.py`

### External
- No external dependencies

## Notes

### Model preset resolution
- Model preset resolution should happen at job start time
- Use the same resolution logic as session model preset
- Ensure consistency with existing model preset handling

### Session metadata
- Model preset should be stored in session metadata
- Use existing `SESSION_MODEL_PRESET_METADATA_KEY`
- Ensure backward compatibility with existing sessions

### Error handling
- Invalid model preset should fall back to session default
- Log warnings for invalid model preset references
- Provide clear error messages in WebUI