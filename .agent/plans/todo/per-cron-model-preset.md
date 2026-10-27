# R-002 — Per-cron model preset selection

## Summary
Implement per-cron model preset selection, allowing each scheduled task to specify its own model preset independent of the session default.

## Current State
Cron jobs execute agent turns but don't have a way to specify a model preset. They use the session's default model preset from the session metadata.

## Implementation Plan

### 1. Core Changes

#### A. Update CronPayload type (nanobot/cron/types.py)
- Add `model_preset: str | None = None` field to `CronPayload` class
- Update `from_store_dict` method to handle the new field
- Update serialization in `_write_store` method

#### B. Update CronJob serialization (nanobot/cron/service.py)
- Update `_write_store` method to include model_preset in payload serialization
- Update `_normalize_agent_turn_job` to handle model_preset

#### C. Update session creation for cron jobs (nanobot/agent/loop.py)
- Modify `set_session_model_preset` to accept a session_key and model preset name
- Update the cron job execution path to set the session's model preset before running
- Modify `submit_cron_turn` to pass model preset information

#### D. Update WebUI types (webui/src/lib/types.ts)
- Add `model_preset` field to `SessionAutomationJob` interface
- Update `AutomationUpdatePayload` to include model_preset
- Update `SessionAutomationJob` serialization in session_automations.py

#### E. Update WebUI API (webui/src/lib/api.ts)
- Add model_preset field to automation update payloads
- Update API endpoints to handle model_preset

#### F. Update WebUI components
- Add model preset selector to automation editor
- Add validation for model preset references
- Update automation form to show model preset field

### 2. Validation and Error Handling

#### A. Model preset validation
- Validate that referenced model preset exists in the preset catalog
- Handle invalid model preset references gracefully
- Provide fallback to session default when model preset is invalid or missing

#### B. Session binding
- Ensure model preset is properly set when session is created for cron job
- Handle model preset changes during job execution
- Ensure model preset is persisted with session metadata

### 3. Testing

#### A. Unit tests
- Test CronPayload serialization with model_preset
- Test CronJob creation with model_preset
- Test model preset validation
- Test session model preset setting

#### B. Integration tests
- Test cron job execution with model preset
- Test model preset fallback behavior
- Test WebUI automation editor with model preset
- Test API endpoints with model_preset

#### C. End-to-end tests
- Test full workflow: create cron job with model preset → execute → verify model preset used

### 4. WebUI Changes

#### A. Automation Editor
- Add model preset dropdown to automation form
- Show available model presets from the preset catalog
- Add validation for model preset selection

#### B. Automation List
- Display model preset for each automation in the list
- Add column for model preset in automation table

#### C. Automation Details
- Show model preset in automation details view
- Allow editing of model preset in automation details

### 5. Backward Compatibility

#### A. Default behavior
- If model_preset is not specified, fall back to session default
- Existing cron jobs continue to work without modification

#### B. Migration
- No migration needed for existing jobs
- New jobs can optionally specify model_preset

### 6. Files to Modify

#### Core Code
- `nanobot/cron/types.py` - Add model_preset to CronPayload
- `nanobot/cron/service.py` - Update serialization and validation
- `nanobot/agent/loop.py` - Update session creation for cron jobs
- `nanobot/session/model_selection.py` - Ensure model preset metadata is handled

#### WebUI
- `webui/src/lib/types.ts` - Add model_preset to automation types
- `webui/src/lib/api.ts` - Update API endpoints
- `webui/src/lib/nanobot-client.ts` - Update client-side automation handling
- `webui/src/components/automation-editor.tsx` - Add model preset field
- `webui/src/components/automation-list.tsx` - Display model preset

#### Tests
- `tests/cron/test_cron_service.py` - Add tests for model_preset
- `tests/webui/` - Add WebUI tests for model_preset
- `tests/agent/` - Add agent loop tests for model_preset

### 7. Verification

#### A. Acceptance Criteria
- [ ] Cron job definition can reference a model preset by name
- [ ] Gateway resolves the preset at job start and uses it for that job's session
- [ ] If no preset is specified, the job falls back to the session default
- [ ] WebUI and TUI show the preset field when editing a cron job
- [ ] Python tests, WebUI checks, and TUI checks pass

#### B. Testing
- [ ] Unit tests for CronPayload with model_preset
- [ ] Integration tests for cron job execution with model_preset
- [ ] WebUI tests for automation editor with model_preset
- [ ] End-to-end tests for full workflow

### 8. Dependencies

#### A. Required
- Model preset catalog must be available during cron job execution
- Session manager must support model preset metadata
- Runtime resolver must support preset selection

#### B. Optional
- Model preset validation can be deferred to runtime
- Invalid model preset can fall back to session default

### 9. Risk Mitigation

#### A. Model preset validation
- Validate model preset exists before job execution
- Fall back to session default if model preset is invalid
- Log warnings for invalid model preset references

#### B. Session binding
- Ensure model preset is set before session is used
- Handle race conditions between model preset setting and job execution
- Ensure model preset is persisted with session metadata

#### C. Performance
- Model preset validation should be cached
- Session model preset setting should be efficient
- No performance impact on existing cron jobs

### 10. Timeline

#### Phase 1: Core Implementation (Week 1-2)
- Update CronPayload type
- Update CronJob serialization
- Update session creation for cron jobs

#### Phase 2: WebUI Integration (Week 3)
- Update WebUI types
- Update WebUI API
- Update WebUI components

#### Phase 3: Testing (Week 4)
- Write unit tests
- Write integration tests
- Write end-to-end tests

#### Phase 4: Verification (Week 5)
- Run all tests
- Verify acceptance criteria
- Fix any issues

### 11. Dependencies

#### A. Internal
- `nanobot/cron/types.py`
- `nanobot/cron/service.py`
- `nanobot/agent/loop.py`
- `nanobot/session/model_selection.py`

#### B. External
- No external dependencies

### 12. Notes

#### A. Model preset resolution
- Model preset resolution should happen at job start time
- Use the same resolution logic as session model preset
- Ensure consistency with existing model preset handling

#### B. Session metadata
- Model preset should be stored in session metadata
- Use existing `SESSION_MODEL_PRESET_METADATA_KEY`
- Ensure backward compatibility with existing sessions

#### C. Error handling
- Invalid model preset should fall back to session default
- Log warnings for invalid model preset references
- Provide clear error messages in WebUI

### 13. Implementation Steps

#### Step 1: Update CronPayload
1. Add `model_preset: str | None = None` to `CronPayload` class
2. Update `from_store_dict` method
3. Update serialization in `_write_store`

#### Step 2: Update CronJob
1. Update `_normalize_agent_turn_job` to handle model_preset
2. Update `_write_store` to include model_preset
3. Update `_read_store` to handle model_preset

#### Step 3: Update Session Creation
1. Modify `set_session_model_preset` to accept session_key
2. Update cron job execution to set session model preset
3. Ensure model preset is persisted

#### Step 4: Update WebUI
1. Add model_preset to SessionAutomationJob
2. Update AutomationUpdatePayload
3. Update API endpoints
4. Update WebUI components

#### Step 5: Testing
1. Write unit tests
2. Write integration tests
3. Write end-to-end tests
4. Run all tests

#### Step 6: Verification
1. Verify acceptance criteria
2. Fix any issues
3. Deploy changes