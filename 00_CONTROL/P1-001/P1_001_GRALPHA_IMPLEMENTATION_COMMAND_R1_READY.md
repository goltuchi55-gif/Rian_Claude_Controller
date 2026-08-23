---
document_id: P1_001_GRALPHA_IMPLEMENTATION_COMMAND_R1
document_type: CONTROLLER_COMMAND
change_id: P1-001
phase: P1
issued_by: RIAN_CONTROLLER
assigned_group: Grα
c4_role: IMPLEMENTER
status: READY
---

# P1-001 Grα Implementation Command R1

## MISSION
Build the local Controller skeleton and runtime-supervision layer so bounded work can be started, observed, recovered, and completed without Human copy/paste or manual Claude wake as a runtime dependency.

## SUCCESS_CONDITION
P1 is implementation-complete only when all are demonstrated in local/mock scope:
1. Local mock E2E PASS.
2. Restart/recovery PASS.
3. `runtime_status.json` accurately matches observed OS/process state.
4. AUDIT material is structurally absent from IMPLEMENTER workspaces.
5. Remote Ops disconnect does not corrupt state or advance phase state.
6. Dedicated single-emitter custody relay is structurally verifiable.
7. Self-test + negative/adversarial tests PASS with reproducible Evidence.

## OUT_OF_SCOPE
- P2 RIAN Adapter logic beyond interfaces needed for P1 mocks.
- P3 full Claude Direct Bridge/group orchestration.
- Production or SHADOW operation.
- Live trading, order execution, money movement, credentials/secrets, live external sends.
- UI/Control Tower.
- Canonical C1-C4 modification.
## AUTHORITY
- ACTIVE C1-C4 + OPERATING_PROFILE through the previously Human-authorized R8 exact-byte Git read/use copy.
- `00_CONTROL/ROADMAP.md` revision 2.
- P0.5 Controller Closeout commit `a9143bf0ca596078b0d02d8661b41de584c70142`.
- P0-C through P2 standing Human authorization remains active; no discretionary Human Gate is inserted for P1.
- Non-waivable Production/credential/financial/canonical boundaries remain unchanged.

## HUMAN_DECISIONS CARRIED FORWARD
- F-5: P1 MUST implement a dedicated, structurally verifiable single-emitter custody relay; do not claim P0.5 already had it.
- NF-1 decision is P0.5-only and MUST NOT auto-extend to P1.
- Git is Control/Handoff/Evidence/Historian, not Production runtime/deploy bus.

## P1 MUST
1. Durable state/WAL and explicit state machine.
2. COMMAND / RESULT / AUDIT envelope separation.
3. Sequence, deduplication, lock/lease, restart-safe intent and decision replay.
4. `START_REQUEST` intent and atomic `RESULT_READY` / `AUDIT_READY` markers.
5. Worker Registry + heartbeat + PID/process reconciliation.
6. `runtime_status.json` with expected/running/stale counts, group/role/function/stage, command SHA, lease state, unmanaged-worker detection, Local Controller health, Remote Ops health.
7. Remote Ops is optional supervisory/commissioning/recovery only; disconnect cannot mutate or advance durable phase state.
8. Path-filtered/sparse custody so AUDIT content cannot materialize into IMPLEMENTER envelope.
9. Dedicated deterministic single-emitter custody relay with allowlisted manifest and exact-byte verification.
10. Repository/per-command `core.autocrlf=false`; no global Git config change.
11. No blind resend after timeout; idempotency and late-result handling MUST be tested.
12. Fail-closed on unexpected FAIL, identity mismatch, unknown dependency, unmanaged worker, stale lease, forged/partial READY marker, or new load-bearing UNKNOWN.
## EXECUTION RULES
- Start read-only: inspect P0.5 local implementation and current P1 workspace before changing anything.
- Minimal change only. No opportunistic refactor, renaming, structure cleanup, or unrelated fixes.
- Reuse only P0.5 components whose purpose and behavior are proven by code/tests; do not import AUDIT artifacts.
- Grα may use Maker / Checker / Internal QA internally, but this is never independent audit.
- If an unexpected FAIL, new dependency, or scope conflict appears, STOP and report. Do not add exceptions, skip tests, weaken thresholds, or change acceptance criteria.
- Keep implementation source local under `C:\Projects\RIAN_CLAUDE_BRIDGE_P1_001_20260823\10_IMPLEMENTER\`.
- Do not publish implementation source to the public handoff repository.
- Evidence handoff must be separated from implementation source and use the custody rules above.

## REQUIRED TESTS
- Normal local mock E2E.
- Controller restart during active intent.
- Worker crash/recovery and stale lease recovery.
- Duplicate START_REQUEST / duplicate result.
- Late result after timeout.
- Forged/partial READY marker.
- Heartbeat loss / PID reuse / unmanaged Claude process.
- Remote Ops disconnect while work is active.
- Negative proof that AUDIT paths are absent from IMPLEMENTER workspace.
- Single-emitter proof that only the custody relay can perform authorized remote evidence deposit.

## RETURN TO RIAN
Return only after implementation/self-test/internal QA are complete:
- STATUS
- IMPLEMENTATION_ROOT
- SELF_TEST
- NEGATIVE_TEST
- LOCAL_MOCK_E2E
- RESTART_RECOVERY
- RUNTIME_STATUS_OS_MATCH
- AUDIT_ISOLATION
- SINGLE_EMITTER_CUSTODY
- OPEN_MUST
- LOAD_BEARING_UNKNOWN
- KNOWN_RESIDUALS
- EVIDENCE_PATHS
- IMPLEMENTATION_IDENTITY / manifest SHA

Do not start Grβ yourself. RIAN will independently verify Grα Evidence and then launch fresh Grβ.