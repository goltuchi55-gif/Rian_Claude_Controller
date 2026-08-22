---
document_id: P0_5_001_AUDITOR_EXPECTATION_COMMAND_R1
document_type: CONTROLLER_COMMAND
revision: 1
change_id: P0_5-001
phase: P0.5
issued_by: RIAN_CONTROLLER
role: CLAUDE_B
c4_role: AUDITOR
stage: EXPECTATION
issued_at_jst: 2026-08-23T00:19:30+09:00
status: FROZEN
---

# P0.5-001 Auditor Expectation Command R1

## MISSION

Independently author and seal the Full-Audit expectation for the P0.5 local feasibility build before any BUILD disclosure.

## ALLOWED INPUTS BEFORE SEAL

Authenticate and read only:
1. ACTIVE C1-C4 / OPERATING_PROFILE through the R8-authorized read/use copy.
2. `00_CONTROL/P0_5-001/P0_5_001_CONTROLLER_PHASE_DEFINITION_R1_20260823.md`.
3. `00_CONTROL/P0_5-001/P0_5_001_IMPLEMENTATION_COMMAND_R3_20260823.md`.
4. Human/control-layer authority artefacts needed to authenticate those documents.

Do not read:
- `05_EVIDENCE/P0_5-001/IMPLEMENTATION/**`;
- `C:\Projects\RIAN_CLAUDE_BRIDGE_P0_5_001_20260823\10_IMPLEMENTER\**`;
- any implementation source/result/log/manifest;
- any prior P0.5 finding or verdict.

## EXPECTATION REQUIREMENTS

Author the expectation yourself. It must include:
- seal-order declaration: exactly what was read and not read;
- target identity/freeze requirements;
- declared write-envelope checks;
- N-3 write isolation and out-of-envelope negative controls;
- WAKE-only scope: one bounded cycle, fresh subprocess, exact SHA authentication, terminal state;
- prohibition on live model request, signed Gate, secrets, Production, finance and canonical change;
- headless CLI feasibility evidence rules;
- RIAN Adapter claim-discipline rules;
- timeout/late/idempotency fail-closed criteria and no blind resend;
- custody single-push-actor boundary and authorized Git paths;
- `core.autocrlf=false` / exact-byte integrity checks;
- rollback;
- self-test evidence quality;
- audit start/end manifest recomputation;
- PASS/FAIL, OPEN_MUST, LOAD_BEARING_UNKNOWN;
- Article 33 T1-T5 / Secondary-Audit trigger assessment;
- correlated-failure limitation.

## LOCAL EXPECTATION PATH

Write only:

`C:\Projects\RIAN_CLAUDE_BRIDGE_P0_5_001_20260823\40_AUDIT\P0_5_001_AUDIT_EXPECTATION_R1_20260823.md`

and its detached `.sha256`.

Do not create or modify BUILD artefacts.

## CUSTODY

Using only the approved clean-clone/bootstrap custody pattern, deposit the exact expectation bytes and sidecar to:

`05_EVIDENCE/P0_5-001/AUDIT/EXPECTATION/CUSTODY_PENDING/`

No force-push, no unrelated repository change, `core.autocrlf=false`.

After deposit, STOP before BUILD disclosure.

## RETURN

STATUS=
EXPECTATION_PATH=
EXPECTATION_SHA256=
T1=
T5=
SECONDARY_AUDIT_REQUIRED=
OPEN_MUST=
GIT_COMMIT_SHA=
