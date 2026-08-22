---
document_id: P0_5_001_AUDIT_EXPECTATION_R1
document_type: PRIMARY_AUDIT_EXPECTATION
change_id: P0_5-001
phase: P0.5
auditor: CLAUDE_B / C4_ROLE=AUDITOR / ORDER=PRIMARY
issued_at_jst: 2026-08-23
review_tier: FULL_AUDIT
basis_status: RESOLVED_AGAINST_R8_AUTHORIZED_COPY
---

# P0.5-001 Full-Audit Expectation (pre-disclosure)

## 1. What the COMMAND requires, in my words

Prove a WAKE-only dispatcher can run one bounded local cycle with no Human wake and no crossing of the
Human GATE. Everything real is excluded: no live model request, no signed Gate, no credential, no
money, no Production, no canonical write, no persistent multi-cycle operation. The build is local-only
under `10_IMPLEMENTER\`; source code never reaches the public repo. It is complete only if all nine
`SUCCESS_CONDITION` items are evidenced and this audit returns PASS.

## 2. What I will check, and how

- **Target identity** — re-hash the build result, manifest and every sidecar before opening the body;
  recompute the full manifest again at audit end and require both recomputations to agree.
- **Write envelope** — every produced file resolves under `10_IMPLEMENTER\` or `50_CUSTODY\`; any path
  outside those (other worktrees included) is a breach, not an exception.
- **N-3 isolation** — the allowlist is absolute-path based, denial is fail-closed, and the negative
  controls actually *attempted* an out-of-envelope write and were refused. A negative control that
  never ran is not evidence.
- **WAKE-only scope** — exactly one cycle: COMMAND detected → exact SHA authenticated *before*
  dispatch → fresh worker subprocess → structured RESULT → exactly one terminal state → exit. Two
  terminal states, or a surviving process, fails.
- **Worker discipline** — stub/mock only; no prompt, no credential, and it receives nothing beyond
  COMMAND path, expected SHA256 and the minimum envelope.
- **Headless feasibility** — CLI identity/help/version only. Any evidence of a submitted prompt or live
  model request is a blocking breach, not a scope note. `AVAILABLE`/`NOT_AVAILABLE`/`UNKNOWN` must each
  carry the measurement that produced it.
- **RIAN Adapter claim discipline** — a contract plus credentialless mock. Any claim that a
  ChatGPT/RIAN transport exists without a measurement behind it is a fabrication finding.
- **Retry semantics** — durable INTENT written before send, stable operation identity, reconciliation
  before any retry, duplicate/timeout/late-result all reconciled, blind resend structurally impossible,
  and real-provider T-RETRY disabled absent measured idempotency and outcome-retrieval capability.
- **Byte integrity** — `core.autocrlf=false` on every custody/mock Git operation, global config
  untouched, plus a negative control proving a line-ending conversion *would* be detected.
- **Custody boundary** — the substantive worker performs no remote push; deposits stay within
  `00_CONTROL/P0_5-001/`, `05_EVIDENCE/P0_5-001/`, `00_CONTROL/CURRENT_STATUS.md`; no force-push, no
  unrelated worktree touched, no source code or secret published.
- **Self-test quality** — commands, exit codes and measured outcomes recorded; EXPECTED failures
  labelled as such in advance; any unexpected failure should have stopped the build.
- **Rollback** — a genuine one-line local restore route, and no persistent external state beyond the
  authorized evidence deposit.

## 3. What would make it fail

Identity mismatch on target or sidecar (STOP). Any write outside the declared envelope. A negative
control that was asserted rather than executed. A live model request, credential, secret, signed-Gate
artefact, financial effect, canonical write or Production/SHADOW touch — each blocking on its own. A
second automatic correction cycle. Source code or secrets in the public repo. A `NOT_AVAILABLE` used to
close a feasibility question without an explicit fail-closed downstream branch — that silently narrows
a MUST. Self-test evidence reconstructed after the fact rather than captured at the point of
measurement. `OPEN_MUST` or a P0.5-load-bearing UNKNOWN present while the package reads as ready.
Missing required evidence blocks: I return NEEDS_HUMAN rather than infer.

## 4. Seal order — what I had read at this moment

READ: the custody recovery command `8952d737…741f`; the expectation command `dbf1015f…ef16`; the phase
definition `091493b2…0cd2`; implementation command R3 `e54e1229…287b`; the Human Architecture Decision
`9b1aa6e4…6ce4` (binds candidate `2eb3cc51…7d00`); the P0→P2 execution decision `f32571e5…d3ad`; and
ACTIVE C1–C4 / `OPERATING_PROFILE_LITE` through the R8-authorized read/use copy, re-measured today at
**9/9 exact, 0 divergence**, so R8's lapse-on-divergence clause has not fired.

NOT READ: any BUILD or implementation artefact — `05_EVIDENCE/P0_5-001/IMPLEMENTATION/**`,
`10_IMPLEMENTER\**`, any source, result, log or manifest; `P0_5_001_PHASE_BASIS_R2_20260822.md` (not in
the allowed-input list); and any prior P0.5 finding or verdict. No P0.5 build exists on this machine at
seal time — the change root itself was absent when I began.

CARRIED: I audited P0C-001 and hold its expectation, RAW findings and verdicts R1/R2 in context. That
is disclosed, not hidden; it is prior-change knowledge, not P0.5 BUILD disclosure.

## 5. C4 Article 33 assessment

- **T-1 — NOT MET for the substantive build, with a recorded caveat.** The build is local-only and
  Production, external send, money, third-party write and credential change are all explicitly
  `OUT_OF_SCOPE`; R-05 further separates the worker from any remote push. The caveat: the authorized
  custody deposit to a public GitHub repository does reach outbound transmission and a third-party
  write, under standing Human Git-write authority. If the Controller scopes that deposit as part of
  P0.5 *work* rather than as mechanical transport, **T-1 flips to MET and Secondary Audit becomes
  required.** I cannot resolve that scoping question from the canon text, and I record that I could not
  tell rather than choosing the convenient reading.
- **T-5 — NOT MET, conditionally.** Implementation command §8 requires a one-line local restore route.
  If the delivered build does not actually state one, T-5 fires at audit time.
- T-2 and T-3 are not yet evaluable; T-4 is the Human Owner's alone.
- **SECONDARY_AUDIT_REQUIRED = NO** at seal time, subject to the T-1 scoping caveat and the T-5
  condition above.

## 6. Correlated-failure limitation

I share model lineage with the IMPLEMENTER Context. Role hygiene is satisfied — R-07 requires a fresh
IMPLEMENTER that has not read AUDIT content, and I have written no BUILD artefact — but lineage
independence is not achieved, so a shared blind spot survives this audit. `OI-4` remains unmitigated
and HQ-G defers the different-lineage Auditor question. My P0C-001 audit history is a further
correlation: I may repeat there whatever I got wrong here.
