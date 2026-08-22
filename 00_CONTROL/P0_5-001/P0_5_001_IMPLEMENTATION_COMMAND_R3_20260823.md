---
document_id: P0_5_001_IMPLEMENTATION_COMMAND_R3
document_type: CONTROLLER_COMMAND
revision: 3
change_id: P0_5-001
phase: P0.5
issued_by: RIAN_CONTROLLER
role: CLAUDE_A
c4_role: IMPLEMENTER
stage: LOCAL_FEASIBILITY_BUILD
issued_at_jst: 2026-08-23T00:19:30+09:00
status: FROZEN
---

# P0.5-001 Implementation Command R3

## MISSION

Implement the narrow P0.5 local feasibility package defined by `P0_5_001_CONTROLLER_PHASE_DEFINITION_R1_20260823.md`, proving a WAKE-only dispatcher path without crossing the Human GATE or any non-waivable boundary.

## PRECONDITIONS

Authenticate by SHA before reliance:
1. `00_CONTROL/P0_5-001/P0_5_001_CONTROLLER_PHASE_DEFINITION_R1_20260823.md` and sidecar.
2. `00_HUMAN/P0C-001/P0C_001_HUMAN_ARCHITECTURE_DECISION_APPROVE_20260822.md`.
3. `00_CONTROL/P0C-001/P0_TO_P2_AUTONOMOUS_EXECUTION_DECISION_20260822.md`.
4. ACTIVE C1-C4 / OPERATING_PROFILE via the R8-authorized Git read/use copy.

Do not read any P0-C or P0.5 AUDIT body, expectation, RAW finding or verdict. Human/control-layer restatements are sufficient.

Use a fresh IMPLEMENTER Context. If this Context has previously read AUDIT content, acted as AUDITOR, or cannot establish role hygiene, STOP before BUILD.

## WRITE ENVELOPE

Substantive IMPLEMENTER writes only under:

`C:\Projects\RIAN_CLAUDE_BRIDGE_P0_5_001_20260823\10_IMPLEMENTER\`

Custody-process writes only under:

`C:\Projects\RIAN_CLAUDE_BRIDGE_P0_5_001_20260823\50_CUSTODY\`

No other local write prefix is authorized except normal OS/process temporary files created by the invoked tools themselves. Do not modify existing project worktrees.

## IMPLEMENTATION SCOPE

Build the smallest dependency-light local prototype, preferably using the standard library unless a measured need requires otherwise.

Required capabilities:

1. **Write isolation / N-3**
   - explicit absolute-path allowlist;
   - deny out-of-envelope target paths fail-closed;
   - negative-control tests.

2. **WAKE-only dispatcher**
   - observes a local mock command source or dedicated clean local Git mock source;
   - detects one new COMMAND;
   - verifies exact SHA256 before dispatch;
   - launches a fresh worker subprocess;
   - accepts structured RESULT;
   - records exactly one terminal completion state;
   - exits after one cycle.

3. **Worker**
   - local deterministic stub/mock only in P0.5;
   - no live Claude prompt/request;
   - no credential use;
   - receives only COMMAND path + expected SHA256 + minimum execution envelope.

4. **Headless Claude feasibility measurement**
   - measure only local CLI identity/help/capability, e.g. executable presence, version and documented non-interactive option;
   - do not submit a prompt or make a live model request;
   - return AVAILABLE / NOT_AVAILABLE / UNKNOWN with evidence.

5. **RIAN Adapter feasibility**
   - define a local interface/mock contract;
   - do not claim an unavailable ChatGPT/RIAN API exists;
   - classify real transport as AVAILABLE / NOT_AVAILABLE / UNKNOWN based only on measured capability.

6. **Timeout / late-response / idempotency simulator**
   - durable INTENT;
   - stable operation identity;
   - duplicate result;
   - timeout;
   - late result;
   - post-hoc reconciliation in the mock;
   - blind resend impossible;
   - real-provider retry disabled unless capability is measured.

7. **Byte integrity**
   - use `core.autocrlf=false` for any custody/mock Git operation;
   - add a negative control proving line-ending conversion would be detected.

8. **Rollback**
   - one-line local restore route;
   - no persistent external state except the authorized evidence handoff.

## OUT OF SCOPE / STOP

STOP before:
- Production or SHADOW action;
- live Claude/model prompt/request;
- signed Human Gate generation/activation/simulation;
- credential/secret/token/key handling;
- financial/trading/payment/order behavior;
- canonical modification;
- non-authorized remote write;
- force-push/history rewrite;
- reading AUDIT material.

## SELF TEST

Run local functional, E2E and negative/adversarial tests covering all required capabilities. Record commands, exit codes and measured outcomes. EXPECTED failures must be explicitly labelled; unexpected failure => STOP.

## BUILD OUTPUT

Create under the IMPLEMENTER envelope:
- source files;
- test files;
- local run logs;
- `P0_5_001_IMPLEMENTATION_RESULT_R1_20260823.md`;
- `P0_5_001_BUILD_MANIFEST_R1.tsv`;
- detached SHA256 sidecars for the result and manifest.

The result must state:
- BUILD_PATH
- WRITE_ENVELOPE
- FILE_LIST
- SELF_TEST
- NEGATIVE_TEST
- N3_WRITE_ISOLATION
- HEADLESS_CLAUDE_FEASIBILITY
- RIAN_API_FEASIBILITY
- IDEMPOTENCY_TIMEOUT_LATE_RESPONSE
- CREDENTIALLESS_MOCK_E2E
- WAKE_TRIGGER_REMOVAL
- CORE_AUTOCRLF_CONTROL
- ROLLBACK
- OPEN_MUST
- LOAD_BEARING_UNKNOWN
- HUMAN_DECISION_REQUIRED_NOW
- PRODUCTION_IMPACT

## HANDOFF

Do not publish implementation source code to the public handoff repository.

After self-tests complete, use only the approved bootstrap custody pattern / deterministic custody process to deposit:
- implementation result,
- build manifest,
- their sidecars,
- a file-list/identity summary sufficient for Controller custody,

to:

`05_EVIDENCE/P0_5-001/IMPLEMENTATION/BUILD_READY/`

Do not deposit secrets, source code, prompt content or unrelated files.

Then STOP at BUILD_READY. Do not read the AUDITOR expectation or perform self-audit.

## RETURN

STATUS=
BUILD_PATH=
SELF_TEST=
NEGATIVE_TEST=
HEADLESS_CLAUDE_FEASIBILITY=
RIAN_API_FEASIBILITY=
WAKE_TRIGGER_REMOVAL=
OPEN_MUST=
LOAD_BEARING_UNKNOWN=
HUMAN_DECISION_REQUIRED_NOW=
RESULT_SHA256=
GIT_COMMIT_SHA=
