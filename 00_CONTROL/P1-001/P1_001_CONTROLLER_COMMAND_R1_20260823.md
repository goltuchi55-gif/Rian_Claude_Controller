---
document_id: P1_001_CONTROLLER_COMMAND_R1
document_type: CONTROLLER_COMMAND
revision: 1
change_id: P1-001
phase: P1
issued_by: RIAN_CONTROLLER
issued_at_jst: 2026-08-23T13:31:00+09:00
status: ACTIVE
assignee: GR_ALPHA
c4_role: IMPLEMENTER
scope: LOCAL_DEV_MOCK_ONLY
upstream_gate_commit: a9143bf0ca596078b0d02d8661b41de584c70142
upstream_gate_sha256: 53556dd5bbce9d738c8a17e1abf78869e1547d4f9b20cb32dc8f5509e3c7079f
---

# P1-001 Controller Command R1

## MISSION

Implement the P1 Local Controller skeleton and runtime-supervision layer as a bounded DEV/local/mock change. Grα is the IMPLEMENTER. RIAN remains CONTROLLER only. Grβ remains reserved for fresh independent audit after BUILD_READY custody.

## SUCCESS_CONDITION

P1 may be presented as BUILD_READY only when all of the following are evidenced:

1. Durable state/WAL and deterministic state-machine transitions exist for the bounded mock flow.
2. START_REQUEST, COMMAND/RESULT/AUDIT envelopes, sequence/dedup, lock/lease, restart-safe replay, and atomic `RESULT_READY` / `AUDIT_READY` marker handling are implemented.
3. Worker Registry, heartbeat, PID/process reconciliation, unmanaged-Claude detection, Local Controller health, and machine-readable `runtime_status.json` are implemented.
4. A structurally verifiable dedicated single-emitter custody relay exists; do not claim the P0.5 mechanism already satisfied this P1 requirement.
5. Path-filtered/sparse custody structurally prevents `AUDIT/**` from materializing in the IMPLEMENTER workspace.
6. Exact-byte / line-ending integrity is verified and blind resend is refused.
7. Local mock E2E PASS and restart/recovery PASS are fixed as evidence.
8. `runtime_status.json` is shown to match measured OS/process state.
9. Remote Ops disconnect/reconnect does not itself corrupt, advance, or mutate runtime phase state.
10. No Production, outbound/external send, credential/secret, financial/trading/order, or canonical-text effect occurs.
11. BUILD_READY evidence contains no unresolved load-bearing MUST/UNKNOWN.

## OUT_OF_SCOPE

- Production operation or promotion.
- Outbound transmission/external send beyond already-authorized repository custody mechanics.
- New third-party write authority.
- Credential addition/change/revocation or secret-value handling.
- Direct money/payment/purchase/trading/order effects, or modification of software that directly executes/moves money.
- Canonical C1-C4 or OPERATING_PROFILE modification.
- P2 real autonomous RIAN transport.
- P3 Claude orchestration as a completion requirement.
- RIAN implementation work or Grα performing independent audit.

## AUTHORITY

Work is governed by the ACTIVE canonical C1-C4/OPERATING_PROFILE and the following recorded authorities/evidence:

- `00_CONTROL/P0C-001/P0_TO_P2_AUTONOMOUS_EXECUTION_DECISION_20260822.md`
  - commit `9edc788043a2e980bb3811ac40a1ff25cb437269`
  - authorizes bounded autonomous execution and automatic phase transition through P2 subject to objective gates.
- `00_HUMAN/P0C-001/P0C_001_HUMAN_ARCHITECTURE_DECISION_APPROVE_20260822.md`
  - commit `cbf0d193f7f6302843815e1912e3699647f1e182`
  - SHA256 `9b1aa6e42f4a50c2bbd69606730cca225d54e46e7e0bad1006420cf50fdf6ce4`
  - adopts the exact P0-C architecture candidate and keeps through-P2 autonomy active.
- `00_CONTROL/P0_5-001/P0_5_001_CONTROLLER_CLOSEOUT_R1_20260823.md`
  - commit `a9143bf0ca596078b0d02d8661b41de584c70142`
  - SHA256 `53556dd5bbce9d738c8a17e1abf78869e1547d4f9b20cb32dc8f5509e3c7079f`
  - P0.5 CLOSED; P1_START_PERMITTED.
- `00_CONTROL/ROADMAP.md` revision 2 and its detached SHA sidecar remain the active implementation roadmap unless superseded by a later valid Controller artifact.

Before implementation, re-measure the referenced authority identities and STOP on mismatch.

## HUMAN_DECISIONS

- Human Owner has already authorized autonomous P1 execution within the bounded DEV/local/mock scope.
- No additional Human Gate is inserted merely because P1 has started.
- Non-waivable Human boundaries remain unchanged.
- The P0.5-specific Human custody-path decision does not auto-extend into P1.

## P1 CARRY-FORWARD MUST

1. Dedicated single-emitter custody relay must be structurally verifiable.
2. AUDIT content must be structurally absent from the IMPLEMENTER workspace.
3. Git remains handoff/evidence/historian, not the real-time runtime bus and not a Production deploy mechanism.
4. IMPLEMENTER and independent AUDITOR remain separated.
5. Unexpected FAIL, out-of-spec behavior, identity mismatch, unknown dependency, or new load-bearing UNKNOWN => fail-closed STOP.

## WRITE ENVELOPE

Grα may create/modify only P1 implementation/test/evidence material under:

- `01_PRE_DESIGN/P1-001/**`
- `02_CONTRACTS/P1-001/**`
- `03_PROTOTYPE/P1-001/**`
- `04_TEST/P1-001/**`
- `05_EVIDENCE/P1-001/IMPLEMENTER/**`

Grα must not modify:

- `00_CONTROL/**`
- `00_HUMAN/**`
- `05_EVIDENCE/P1-001/AUDIT/**`
- ACTIVE canonical material
- prior immutable P0-C/P0.5 audit/evidence artifacts

Runtime state may exist locally for test execution, but only bounded evidence snapshots belong in the Git evidence envelope above.

## EXECUTION

1. Re-measure authority and this COMMAND identity.
2. Inspect the existing P0.5 prototype/contracts only as inputs; do not rewrite immutable P0.5 evidence.
3. Implement the minimum P1 architecture satisfying the SUCCESS_CONDITION and MUSTs.
4. Run self-test, local mock E2E, restart/recovery, negative/adversarial checks relevant to the P1 scope.
5. Produce manifest and detached SHA256 evidence.
6. Deposit an IMPLEMENTER BUILD_READY result/evidence package under the write envelope.
7. Stop after BUILD_READY custody. Do not author an AUDITOR expectation/verdict and do not self-advance to P2.

The Controller will verify custody and then issue the independent Grβ audit path if the BUILD_READY gate is valid.
