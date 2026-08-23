---
document_id: P2_001_GRALPHA_IMPLEMENTATION_COMMAND_R1
document_type: CONTROLLER_COMMAND
change_id: P2-001
phase: P2
issued_by: RIAN_CONTROLLER
assigned_group: Grα
c4_role: IMPLEMENTER
status: READY
---

# P2-001 Grα Implementation Command R1

## MISSION
Build the P2 logical RIAN Adapter/controller-facing decision layer in credentialless local/mock scope. Do not invent or claim a real autonomous ChatGPT/RIAN API or transport.

## ENTRY GATE / AUTHORITY
- ACTIVE C1-C4 + OPERATING_PROFILE via the R8-authorized exact-byte Git read/use copy.
- P1 Controller Closeout SHA256: `1db01eb87fb83b202266cfd0b423877fe576455d2a16a2b444981c497b097510`.
- P1 independent Grβ verdict: PASS, OPEN_MUST=0, LOAD_BEARING_UNKNOWN=0, BLOCKING_FINDINGS=0, SECONDARY_AUDIT_REQUIRED=NO.
- Standing Human authorization permits P2 within non-waivable boundaries.
- Grα is IMPLEMENTER only. Grβ remains independent AUDITOR. RIAN remains Controller only.

## SUCCESS_CONDITION
1. Controller -> RianAdapter -> DecisionResult deterministic reproduction PASS.
2. Canonical loader exact-identity validation PASS and mismatch/missing cases fail closed.
3. Decision/Human-boundary classification PASS for representative and negative cases.
4. RIAN_INBOX event contract validates and rejects malformed/unsupported inputs.
5. Deterministic replay of identical input/context yields byte-stable DecisionResult.
6. Credentialless mock transport only; no fabricated real autonomous RIAN transport.
7. Self-test and negative/adversarial test suites PASS with reproducible Evidence.
## P2 MUST
1. Define a `RianTransport` interface/contract with an explicit credentialless mock implementation. Real product/API transport remains `NOT_ESTABLISHED`.
2. Implement canonical loader that accepts only the authorized exact-byte authority set and verifies expected SHA identities before use.
3. Implement decision loader for bounded Human Decisions / Controller inputs without modifying their source artifacts.
4. Implement deterministic Gate engine using explicit inputs; no hidden mutable memory may determine a Gate result.
5. Implement Human Action classification including at minimum: routine automated action, NEEDS_HUMAN, non-waivable Production, credential/secret, financial/trading/order, canonical modification, and unsupported/unknown action.
6. Implement a versioned `RIAN_INBOX` event contract with schema/version/change_id/event_id/payload identity and reject malformed, duplicate-conflicting, unknown-version, or unsupported events.
7. Implement `DecisionResult` with deterministic identity/hash, decision, grounds references, required human action, next state, and load-bearing unknowns.
8. Replay must reproduce identical DecisionResult bytes for identical event + exact authority + exact decision set.
9. Changed authority/decision/event identity must produce a changed result identity or fail closed; never silently reuse an old decision.
10. Integrate only through a narrow P1 Controller-facing adapter/interface. Do not alter P1 source unless an objectively necessary interface defect is discovered; if so STOP and report rather than patching P1.
11. No network requirement, no credentials, no live external send, no Production/SHADOW effect, no financial/trading/order execution, no C1-C4 modification.
12. Preserve P1 residual limitations honestly; do not reinterpret local structural guards as OS-level security boundaries.

## OUT_OF_SCOPE
- Real ChatGPT/RIAN autonomous API/product internals.
- Full Claude Direct Bridge / group orchestration (P3).
- Production or SHADOW commissioning.
- UI/Control Tower.
- Any credential provisioning or secret handling.
- Git/public publication of P2 implementation source.
## REQUIRED TESTS
- Deterministic happy-path Controller -> Adapter -> DecisionResult.
- Same input replay repeated multiple times with byte-identical result.
- Canon SHA mismatch, missing canon, altered decision artifact, malformed inbox event.
- Duplicate same event is idempotent; conflicting duplicate fails closed.
- Unknown schema/version/action fails closed.
- Human-boundary matrix covers routine automation vs all non-waivable effects.
- Attempted Production/credential/financial/canonical action produces NEEDS_HUMAN/STOP and no side effect.
- Mock transport disconnect/error/timeout cannot mutate the decision result or durable P1 state.
- Negative proof that no real API/credential/network path is required by P2 candidate.

## CHANGE DISCIPLINE
Read-only investigation first. Reuse P1 interfaces read-only where appropriate. Minimum change only; no unrelated refactor or side-fix. Unexpected FAIL, P1 interface defect, new dependency, or load-bearing UNKNOWN => STOP and report before repair.

## OUTPUT
Keep implementation under `C:\Projects\RIAN_CLAUDE_BRIDGE_P2_001_20260823\10_IMPLEMENTER\`. Produce self-test/negative logs, manifest + SHA256, implementation result, rollback instructions, and atomic `RESULT_READY.json` + sidecar only if all required checks pass. Do not start Grβ.

## RETURN TO RIAN
STATUS, SELF_TEST, NEGATIVE_TEST, ADAPTER_E2E, DETERMINISTIC_REPLAY, CANON_IDENTITY_GUARD, HUMAN_BOUNDARY_CLASSIFICATION, INBOX_CONTRACT, REAL_TRANSPORT_STATUS, OPEN_MUST, LOAD_BEARING_UNKNOWN, BLOCKING_FINDINGS, RESULT_READY_PATH, IMPLEMENTATION_MANIFEST_SHA256, KNOWN_RESIDUALS, UNEXPECTED_FINDINGS.