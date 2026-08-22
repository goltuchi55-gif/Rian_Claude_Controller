---
document_id: P0_5_CLAUDE_A_IMPLEMENTER_COMMAND_R1
document_type: CONTROLLER_COMMAND
phase: P0.5
role: CLAUDE_A
c4_role: IMPLEMENTER
issued_by: RIAN_CONTROLLER
status: ACTIVE
scope: LOCAL_CANDIDATE_MOCK_ONLY
---

# P0.5 CLAUDE_A Implementer Command R1

## Mission

Build the minimum local/candidate/mock technical-feasibility prototype needed to resolve the major P0.5 UNKNOWNs. This is not P1 production-quality implementation.

## Authority / boundaries

Read first:
- `00_CONTROL/P0.5/P0_5_CONTROLLER_PREFLIGHT_R1_20260822.md`
- `00_HUMAN/P0C-001/P0C_001_HUMAN_ARCHITECTURE_DECISION_APPROVE_20260822.md`

Operate only inside a dedicated P0.5 IMPLEMENTER workspace and a candidate Git branch.

Do NOT:
- operate or modify Production;
- send a real Claude/OpenAI/Anthropic model request;
- perform any non-Git third-party write;
- read, print, copy or modify secret/credential values;
- modify canonical text;
- read CLAUDE_B's P0.5 expectation or audit working notes;
- modify P0-C sealed/audit history;
- add external dependencies unless strictly necessary. Prefer Python/PowerShell standard library only.

Git handoff to `goltuchi55-gif/Rian_Claude_Controller` is permitted for this approved P0-P2 test window. Use a dedicated candidate branch; do not merge/promote to main.

## Minimum technical probes

Measure and record, without a real model call:

1. `claude` executable discovery, version, and help/CLI evidence for non-interactive/headless mode. `--version` / `--help` are allowed; do not execute a real prompt.
2. Local process-spawn feasibility for a headless-worker contract using a credentialless mock/shim that emulates request/response/exit-code/timeout behavior.
3. Local dispatcher feasibility with durable state and restart recovery.
4. N-3 write isolation: a worker assigned one output root must be unable to write outside it. Include path-traversal and absolute-path negative controls.
5. Command/result envelope feasibility with at least `command_id`, `sequence`, `role`, `status`, `result_path`, and measured timestamps.
6. Idempotency/dedup: replaying the same `command_id` must not execute the mock side effect twice.
7. Timeout and late-response behavior: timed-out work becomes UNKNOWN/failed-closed and a late response cannot silently overwrite the terminal state.
8. Mock API disconnect/error behavior with no credentials and no network service requirement.
9. Local credentialless mock E2E: COMMAND -> dispatcher -> mock worker -> RESULT -> durable state.
10. Restart/recovery: terminate/restart the dispatcher between command acceptance and result completion, then prove deterministic recovery or explicit UNKNOWN.

## Scope discipline

This phase is a feasibility spike. Do not build P1's full Controller, Rian Adapter, Control Tower, Production deploy path, credential store, or real external API integration.

## Suggested repository layout

Use candidate-only paths such as:
- `03_PROTOTYPE/P0.5/`
- `04_TEST/P0.5/`
- `05_EVIDENCE/P0.5/IMPLEMENTER/`

You may choose a safer equivalent layout.

## Required evidence

Produce:

1. `P0_5_TECH_FEASIBILITY_RESULT_R1.md`
2. `P0_5_TEST_MATRIX_R1.tsv` or `.md`
3. machine-readable evidence for measured test outcomes where practical
4. detached `.sha256` for each load-bearing result/evidence file
5. exact candidate commit SHA

Every number must be labelled MEASURED / ESTIMATED / UNKNOWN with method/source.

The result must explicitly report each P0.5 item as `PASS`, `FAIL`, or `UNKNOWN`, plus residual risks.

## Completion / return

Run the local normal E2E and negative controls. Do not self-audit.

Push the candidate branch and return only:

STATUS=
CANDIDATE_BRANCH=
CANDIDATE_COMMIT_SHA=
RESULT_PATH=
RESULT_SHA256=
TESTS_PASS=
TESTS_FAIL=
TESTS_UNKNOWN=
OPEN_MUST=
LOAD_BEARING_UNKNOWN=
REAL_EXTERNAL_MODEL_CALL_PERFORMED=NO

Then wait for independent audit.
