---
document_id: P0C_001_CURRENT_COMMAND
document_type: CONTROLLER_COMMAND
revision: 1
change_id: P0C-001
issued_by: RIAN_CONTROLLER
scope: PRIMARY_AUDIT_EXPECTATION_CUSTODY
---

# P0-C-001 Current Command

1. Pull `goltuchi55-gif/Rian_Claude_Controller` with fast-forward only.
2. Read:
   - `00_CONTROL/P0C-001/P0C_001_CONTROLLER_RESOLUTION_R8_AND_EXPECTATION_CUSTODY_R1_20260822.md`
   - `00_CONTROL/P0C-001/P0_TO_P2_AUTONOMOUS_EXECUTION_DECISION_20260822.md`
3. Keep the already-authored Primary Audit Expectation bytes unchanged.
4. Push the exact expectation and detached `.sha256` only to:
   `05_EVIDENCE/P0C-001/PRIMARY_AUDIT/CUSTODY_PENDING/`
5. Do not open Alpha/Beta/Gamma or the RIAN consolidated candidate yet.
6. After push, return only:
   `STATUS`, `EXPECTATION_PATH`, `EXPECTATION_SHA256`, `GIT_COMMIT_SHA`.
7. Wait at the custody checkpoint. No Human approval is required at this checkpoint.
