---
document_id: P0C_001_CURRENT_COMMAND
document_type: CONTROLLER_COMMAND
revision: 2
change_id: P0C-001
issued_by: RIAN_CONTROLLER
role: CLAUDE_B
c4_role: AUDITOR
order: PRIMARY
stage: ARTIFACT_AUDIT
scope: P0C_001_PRIMARY_AUDIT
---

# P0-C-001 Current Command R2

1. Pull `goltuchi55-gif/Rian_Claude_Controller` with fast-forward only.
2. Read:
   - `00_CONTROL/P0C-001/P0C_001_CONTROLLER_EXPECTATION_SEAL_ACK_R1_20260822.md`
   - the already-sealed Primary Audit Expectation.
3. Do not modify the sealed expectation.
4. Before reading any audit target body, independently re-hash the intended frozen P0-C-001 audit target and its detached sidecar exactly as required by the sealed expectation.
5. If target identity or sidecar does not reproduce, STOP fail-closed and report the measured identity only.
6. If identity reproduces, perform the Primary Audit read-only against the frozen P0-C-001 target and the permitted shared inputs/evidence under ACTIVE canon.
7. Do not repair or modify the audited deliverable.
8. Do not reopen or modify Grα / Grβ / Grγ.
9. Produce a written Primary Audit finding and detached `.sha256`, including:
   - target identity,
   - MUST findings,
   - UNKNOWN findings,
   - T-2 / T-3 / T-4 / Secondary-Audit trigger status,
   - PASS / FAIL verdict,
   - residual issues.
10. Push only the audit finding, sidecar, and any non-secret audit manifest/evidence needed for verification to:
    `05_EVIDENCE/P0C-001/PRIMARY_AUDIT/RESULT/`
11. After push, stop at the audit-result checkpoint. No Human approval is required at that checkpoint.

Return only:

STATUS=
TARGET_SHA256=
AUDIT_VERDICT=
OPEN_MUST=
LOAD_BEARING_UNKNOWN=
SECONDARY_AUDIT_REQUIRED=
RESULT_PATH=
RESULT_SHA256=
GIT_COMMIT_SHA=
