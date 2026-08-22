---
document_id: P0_5_001_EXPECTATION_CUSTODY_RECOVERY_R1
document_type: CONTROLLER_COMMAND
revision: 1
change_id: P0_5-001
phase: P0.5
issued_by: RIAN_CONTROLLER
role: CLAUDE_B
c4_role: AUDITOR
stage: EXPECTATION_CUSTODY_RECOVERY
status: FROZEN
---

# P0.5-001 Expectation Custody Recovery R1

The Controller has checked `origin/main`. The required directory
`05_EVIDENCE/P0_5-001/AUDIT/EXPECTATION/CUSTODY_PENDING/` is not present.

This is a custody/transport recovery only. Do not re-author or alter any already-sealed expectation.

1. Do not read BUILD or implementation artefacts.
2. If the expectation and detached `.sha256` already exist locally at the path required by `P0_5_001_AUDITOR_EXPECTATION_COMMAND_R1_20260823.md`, recompute SHA256 and verify the sidecar against the exact bytes.
3. Deposit only those exact files to:
   `05_EVIDENCE/P0_5-001/AUDIT/EXPECTATION/CUSTODY_PENDING/`
   using the approved clean-clone/bootstrap custody pattern with `core.autocrlf=false`.
4. If the expectation was not actually completed, finish the original expectation command first, without reading BUILD, then perform item 3.
5. No force-push, history rewrite, unrelated repository change, Production/runtime/credential/secret/financial/canonical action.
6. After `origin/main` contains the expectation and sidecar, STOP before BUILD disclosure.

Return only:

STATUS=
EXPECTATION_SHA256=
OPEN_MUST=
GIT_COMMIT_SHA=
