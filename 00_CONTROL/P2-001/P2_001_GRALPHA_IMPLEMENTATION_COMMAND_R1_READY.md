---
document_id: P2_001_GRALPHA_IMPLEMENTATION_COMMAND_R1
document_type: CONTROLLER_COMMAND
change_id: P2-001
phase: P2
issued_by: RIAN_CONTROLLER
assigned_group: Grα
c4_role: IMPLEMENTER
status: READY
issued_at_jst: 2026-08-23T15:34:00+09:00
---

# P2-001 Grα Implementation Command R1

## MISSION
Implement the logical RIAN Adapter / decision layer in credentialless local-mock scope so the Local Controller can deterministically obtain and replay a `DecisionResult` without fabricating a real autonomous RIAN transport.

## SUCCESS_CONDITION
P2 is implementation-complete only when all are demonstrated in local/mock scope:
1. `Controller -> RianTransport -> DecisionResult` deterministic reproduction PASS.
2. Credentialless mock transport PASS.
3. Canonical loader verifies exact identity before use and fails closed on mismatch/missing authority.
4. Decision loader and replay are deterministic across restart/re-delivery.
5. Gate engine correctly classifies Human-required boundaries and never auto-approves non-waivable actions.
6. `RIAN_INBOX` event contract is machine-readable, deduplicated, and idempotent.
7. No fabricated live RIAN API/transport claim.
8. Self-test + negative/adversarial tests PASS with reproducible Evidence.
9. OPEN_MUST=0 and LOAD_BEARING_UNKNOWN=0 before audit handoff.

## OUT_OF_SCOPE
- P3 live Claude Direct Bridge / group orchestration.
- Production or SHADOW operation.
- Live outbound/external sends beyond the already-authorized Git control handoff used to publish this COMMAND.
- Credential/secret acquisition, mutation, storage, or disclosure.
- Financial/trading/payment/order effects.
- Canonical C1-C4 modification.
- UI / Control Tower.

## AUTHORITY
- ACTIVE C1-C4 + OPERATING_PROFILE under the recorded Human Owner activation/authorization.
- Standing Human authorization for autonomous execution through P2.
- `00_CONTROL/ROADMAP.md` revision 2.
- P1 local Controller closeout: `P1_001_CONTROLLER_CLOSEOUT_R1_20260823.md`, SHA256 `1db01eb87fb83b202266cfd0b423877fe576455d2a16a2b444981c497b097510`.
- P1 Grβ primary verdict SHA256 `246307d169af030d09babf63209ba5ec4558d14f6642475d8f861e220cf9d12c`: PASS, OPEN_MUST=0, LOAD_BEARING_UNKNOWN=0, BLOCKING_FINDINGS=0.

## CARRIED-FORWARD PROCESS FACT
This COMMAND is deposited to the authorized Git handoff repository. Under C4 Article 33, external transmission / third-party write is not waived by permission. Therefore `T-1=MET` for the P2 process-governance path. P2 closure MUST include the required fresh `order: secondary / scope: process` audit after the primary audit RAW is fixed. D-3 applies: secondary must not read primary finding body, grounds, verdict, or reasoning before fixing its own RAW result.

## P2 MUST
1. Define a narrow `RianTransport` contract and a credentialless deterministic mock implementation.
2. A real/autonomous RIAN transport MUST remain explicitly `UNAVAILABLE` unless independently measured; do not simulate availability by renaming the mock.
3. Canonical/authority loader MUST verify path/identity/detached SHA256 and fail closed on mismatch, missing sidecar, ambiguity, or unknown authority.
4. Decision input/output schemas MUST be machine-readable, versioned, and deterministic.
5. Decision replay MUST be idempotent across duplicate request, restart, timeout, and late result.
6. Gate engine MUST classify non-waivable Production / external-send / third-party-write / credential / secret / financial boundaries as Human-required; no default-allow branch.
7. `RIAN_INBOX` event contract MUST have stable event identity, sequence/dedup semantics, and explicit terminal states.
8. Interactive Remote Desktop Commander / PowerShell is attended supervisory/commissioning access only and MUST NOT be treated as autonomous `RianTransport`.
9. Reuse P1 interfaces only where exact purpose/behavior is proven; do not broaden P1 authority or modify P1 audited artifacts.
10. Implementation source remains local under `C:\Projects\RIAN_CLAUDE_BRIDGE_P2_001_20260823\10_IMPLEMENTER\`; do not publish source to the public handoff repository.
11. Keep IMPLEMENTER and AUDIT envelopes disjoint. Grα MUST NOT read P1/P2 AUDIT material.
12. Unexpected FAIL, identity mismatch, unknown dependency, authority ambiguity, or new load-bearing UNKNOWN => fail-closed STOP and report. Do not weaken tests or invent exceptions.

## REQUIRED TESTS
- Deterministic happy-path decision round trip.
- Duplicate request / duplicate decision.
- Restart and replay.
- Timeout then late decision.
- Missing/mismatched detached SHA256.
- Ambiguous/missing canonical authority.
- Unknown or unsupported transport.
- Forged `DecisionResult`.
- Human-boundary classification for Production, external send/third-party write, credential/secret, financial/trading/payment/order cases.
- Remote Ops presence/absence does not change deterministic decision semantics.
- Negative proof that no credential-shaped environment or secret value is required.

## EXECUTION
- Start read-only against P1 interfaces and the ACTIVE authority copies.
- Create only the P2 local workspace/envelope needed for this change.
- Minimal implementation only; no opportunistic refactor or P3 work.
- Grα may perform Maker/Checker/Internal-QA functions internally, but this is not independent audit.
- Do not start Grβ yourself.

## RETURN TO RIAN
Return only after implementation/internal QA are complete:
- STATUS
- IMPLEMENTATION_ROOT
- AUTHORITATIVE_COMMAND_SHA256
- SELF_TEST
- NEGATIVE_TEST
- MOCK_DECISION_E2E
- RESTART_REPLAY
- IDENTITY_FAIL_CLOSED
- HUMAN_BOUNDARY_CLASSIFICATION
- REAL_TRANSPORT_STATUS
- OPEN_MUST
- LOAD_BEARING_UNKNOWN
- KNOWN_RESIDUALS
- EVIDENCE_PATHS
- IMPLEMENTATION_MANIFEST_SHA256
- RESULT_READY_SHA256
