---
document_id: P0_5_CLAUDE_B_EXPECTATION_COMMAND_R1
document_type: CONTROLLER_COMMAND
phase: P0.5
role: CLAUDE_B
c4_role: AUDITOR
order: PRIMARY
stage: EXPECTATION
issued_by: RIAN_CONTROLLER
status: ACTIVE
scope: P0_5_PRE_DISCLOSURE_EXPECTATION_ONLY
---

# P0.5 CLAUDE_B Expectation Command R1

## Mission

Create and seal your own independent audit expectation for the P0.5 technical-feasibility deliverable before reading any CLAUDE_A P0.5 implementation result, candidate branch, code, test output, summary, or evidence.

## Read only before seal

You may read:
- ACTIVE canon / OPERATING_PROFILE via the already-authorized Git read/use copy;
- `00_CONTROL/P0.5/P0_5_CONTROLLER_PREFLIGHT_R1_20260822.md`;
- `00_CONTROL/P0.5/P0_5_CLAUDE_A_IMPLEMENTER_COMMAND_R1_20260822.md`;
- the Human-issued P0-C Architecture approval and autonomous execution decision through P2.

Do NOT read before seal:
- CLAUDE_A's P0.5 candidate branch;
- `03_PROTOTYPE/P0.5/` deliverables;
- `04_TEST/P0.5/` results;
- `05_EVIDENCE/P0.5/IMPLEMENTER/`;
- CLAUDE_A chat/session summary or working notes.

## Expectation requirements

Write the expectation yourself. Keep it short and operational. Include:

1. what P0.5 requires in your own words;
2. what you will check and how;
3. what would fail the audit;
4. seal-order declaration listing what you had and had not read;
5. explicit checks for role separation, write isolation, idempotency/dedup, timeout/late-response fail-closed behavior, restart/recovery, credentialless mock E2E, evidence labels, and proof that no real external model call occurred;
6. expected treatment of any residual real-API/headless-live-call limitation under the P0.5 command rather than silently converting it to PASS.

## Save / custody

Push only the sealed expectation and detached `.sha256` to `main` under:

`05_EVIDENCE/P0.5/AUDIT/EXPECTATION/`

Do not modify P0-C history, CLAUDE_A candidate work, canonical text, Production, runtime, credentials, or external systems.

## Return

After push, stop before opening any P0.5 deliverable and return only:

STATUS=
EXPECTATION_PATH=
EXPECTATION_SHA256=
GIT_COMMIT_SHA=
OPEN_MUST=

Then wait for the Controller's artifact-disclosure command.
