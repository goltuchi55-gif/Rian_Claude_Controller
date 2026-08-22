---
document_id: P0_5_001_CONTROLLER_PHASE_DEFINITION_R1
document_type: CONTROLLER_RESOLUTION
revision: 1
change_id: P0_5-001
phase: P0.5
issued_by: RIAN_CONTROLLER
issued_at_jst: 2026-08-23T00:19:00+09:00
status: ACTIVE
---

# P0.5-001 Controller Phase Definition R1

## MISSION

Resolve the measured P0.5 phase-definition gaps and authorize the narrowest safe local feasibility package that removes the Human WAKE trigger without automating or weakening the Human GATE.

## SUCCESS_CONDITION

P0.5 is complete only when all of the following are evidenced and the required independent Full Audit is PASS:

1. N-3 write-isolation controls and negative controls PASS inside declared local write envelopes.
2. Headless-Claude feasibility is measured locally without sending a live model request: the installed CLI identity/help proves a non-interactive invocation mode is available or returns a measured NOT_AVAILABLE result.
3. RIAN API feasibility is classified by an explicit local adapter contract and credentialless mock. No unavailable API is invented.
4. Timeout, late-response, duplicate-result and idempotency behavior is simulated with durable INTENT and reconciliation; blind resend is impossible; real-provider T-RETRY remains disabled unless provider idempotency/outcome-retrieval capability is separately measured.
5. Credentialless mock E2E PASS.
6. A local WAKE-only dispatcher completes one bounded cycle after process start without a Human wake: COMMAND detection -> exact SHA authentication -> fresh worker subprocess -> RESULT -> durable completion state. The worker is a local stub/mock in P0.5; no live Claude prompt is sent.
7. Dedicated clean custody/worker paths preserve exact bytes with `core.autocrlf=false`; checkout/line-ending negative controls PASS.
8. Full independent audit of the implementation package returns PASS, OPEN_MUST=0 and no P0.5-load-bearing UNKNOWN.
9. No Production, signed Human Gate activation, credential/secret handling, financial/trading/payment/order effect, canonical write, or non-authorized external send occurs.

A measured `NOT_AVAILABLE` result may close a feasibility question only when the fail-closed downstream branch is explicit and does not silently narrow a MUST.

## OUT_OF_SCOPE

- Production or SHADOW adoption.
- Live model prompt/request from the dispatcher.
- Signed Human Gate generation, activation, simulation, key placement or key use.
- Credential, secret, token or private-key handling.
- Financial/trading/payment/order behavior.
- Canonical text changes.
- Persistent multi-cycle unattended operation.
- Any direct modification of QuickTrend money-moving/runtime behavior.

## AUTHORITY

- ACTIVE C1-C4 and OPERATING_PROFILE through the R8-authorized Git read/use copy while activated identities match.
- Human Architecture Decision APPROVE for candidate SHA256 `2eb3cc51f03bc5296f2630a22317d721807cce290392357607111877d56b7d00`.
- P0-C through P2 autonomous execution decision SHA256 `f32571e574368a580c433da76e610f7a18eb2c0d4226d083167ebf44ef7ed3ad`.
- P0.5 Phase Basis Discovery R2 commit `1e09d60326c40fdf17de818e64e578d42312dd65`, sidecar SHA256 `9eb9b7ec628457fdd290952786f0f82db609ccb54472dc5b2a92c21dc2e29686`.
- Human-approved roadmap already established for this execution window:
  - P0.5: technical feasibility; complete when major technical UNKNOWNs are resolved.
  - P1: Controller skeleton; complete on Local mock E2E PASS.
  - P2: RIAN Adapter; complete on autonomous decision reproduction PASS.

## HUMAN_DECISIONS

No new Human decision is required now. The existing P0-P2 execution authorization remains in force. Non-waivable action-specific Human boundaries remain unchanged.

## CONTROLLER RESOLUTIONS

### R-01 — Phase completion gate

The `SUCCESS_CONDITION` above is the objective P0.5 completion gate. It operationalizes the already-approved roadmap phrase “major technical UNKNOWNs resolved” without expanding scope.

### R-02 — P1 definition

P1 scope is limited to a local Controller skeleton: durable state, state machine, COMMAND/RESULT/AUDIT envelopes, sequence, deduplication, lock/lease and decision replay. Completion: Local mock E2E PASS plus any audit required by ACTIVE tier rules.

### R-03 — P2 definition

P2 scope is limited to the RIAN Adapter/controller-facing abstraction: canonical loader, decision loader, Gate engine and Human Action classification. Actual ChatGPT/RIAN product internals or unavailable APIs must not be invented. Completion: autonomous decision reproduction PASS plus any required independent audit.

### R-04 — Authorized Git handoff repository

For P0.5, the only authorized remote handoff repository is:

`goltuchi55-gif/Rian_Claude_Controller`

Authorized remote paths are limited to:
- `00_CONTROL/P0_5-001/`
- `05_EVIDENCE/P0_5-001/`
- `00_CONTROL/CURRENT_STATUS.md`

Implementation source code is local-only in P0.5 and must not be published to the public repository.

### R-05 — Single remote-push actor

The P0.5 substantive worker does not perform Git remote push as part of its work. Remote handoff is performed only by a deterministic `LOCAL_CUSTODY_RELAY` process using a dedicated clean handoff clone and an allowlisted manifest. `LOCAL_CUSTODY_RELAY` is a mechanical custody process, not a new C4 role and not a source of judgment.

Until the audited relay exists, the previously proven clean-clone/bootstrap custody pattern may be used solely to deposit expectation/result/evidence artefacts in the authorized paths. It must operate in a dedicated custody path, with no checkout/reset/stash/clean of unrelated worktrees and no force-push.

### R-06 — Byte integrity

Every P0.5 custody clone/process must use repository-local or per-command `core.autocrlf=false`. Global Git configuration must not be changed. Exact bytes are hashed before handoff and re-hashed after remote deposit.

### R-07 — Implementer context hygiene

The Context that produced Phase Basis Discovery R2 is not eligible to implement the P0.5 build because it disclosed prior audit-adjacent/custody exposure. The build must use a fresh IMPLEMENTER Context that has not read AUDIT content.

### R-08 — Retry unknowns

Real-provider automatic T-RETRY is disabled in P0.5 unless provider idempotency-key and post-hoc outcome-retrieval capabilities are measured. The mock must prove durable INTENT, same operation identity, reconciliation and fail-closed behavior.

### R-09 — Signed Gate unknown

Signing-key unreadability/storage remains OPEN but is not load-bearing for the WAKE-only dispatcher because signed Gate activation is OUT_OF_SCOPE. Any move toward key generation, placement or use requires STOP at the applicable Human boundary.

### R-10 — Human spot-check residual

P0.5 is a single-cycle local feasibility test that auto-stops. It does not authorize persistent unattended operation. Therefore the long-running unattended Human spot-check design is not load-bearing for P0.5 completion. It must be resolved before any persistent multi-cycle unattended mode is enabled.

## REVIEW TIER

`FULL_AUDIT`

A separate AUDITOR Context must author and seal its own expectation before reading the implementation target. No separate pre-implementation Plan audit is added because the ACTIVE tier source does not require one.

## NEXT SAFE ACTION

1. AUDITOR authors/seals the P0.5 expectation from this resolution and the frozen implementation command without reading BUILD.
2. A fresh IMPLEMENTER performs the bounded local implementation and self/negative tests.
3. Controller verifies expectation custody, then releases target disclosure.
4. AUDITOR performs read-only independent audit.
5. Controller verifies audit evidence and decides P0.5 completion against `SUCCESS_CONDITION`.
