---
document_id: P0_5_001_SECONDARY_PROCESS_AUDIT_RAW_FINDINGS_R1
document_type: AUDIT_RAW_FINDINGS
revision: 1
change_id: P0_5-001
phase: P0.5
role: CLAUDE_B
c4_role: AUDITOR
order: secondary
scope: process
stage: artifact
authored_by: SECONDARY_AUDITOR_CONTEXT_FRESH_R2
governing_command: P0_5_001_SECONDARY_PROCESS_AUDIT_RELEASE_COMMAND_R1_20260823.md
governing_command_sha256: 6166a3bbde24c2b255e4426aa21a6aabe5fc7d975f00a550770d0e5caefea888
governing_expectation: P0_5_001_SECONDARY_AUDIT_EXPECTATION_R1_20260823.md
governing_expectation_sha256: 912ba9935dbf1171f05901a1ee27f121d5c6a33861e62b69b2173ccb39ab4fd3
status: RAW_FIXED
---

# P0.5-001 Secondary Process Audit — RAW Findings R1

This is the immutable RAW result. It is not altered after fixation. Every finding states where,
what, how it was found (a re-runnable command or file+line), and whether it blocks.

---

## 0. Authentication (Release Command §REQUIRED AUDIT ACTIONS item 1)

| item | measured SHA256 | matches Controller-stated value |
|---|---|---|
| `P0_5_001_SECONDARY_PROCESS_AUDIT_RELEASE_COMMAND_R1_20260823.md` | `6166a3bbde24c2b255e4426aa21a6aabe5fc7d975f00a550770d0e5caefea888` | matches own sidecar |
| `P0_5_001_SECONDARY_AUDIT_EXPECTATION_R1_20260823.md` | `912ba9935dbf1171f05901a1ee27f121d5c6a33861e62b69b2173ccb39ab4fd3` | MATCH — equals value cited in Release Command line 30, equals sidecar |

Method: `sha256sum` over local bytes, compared to detached sidecar and to the Release Command's
cited value. Both authenticated before substantive review began.

---

## 1. LBU-1 (activation status) — RESOLVED

**Where:** `_AUTHORITY_RELEASE_EXACT/00_PROCESS/ACTIVATION_DECISION_LOG.md`,
`_AUTHORITY_RELEASE_EXACT/00_PROCESS/ACTIVE_POLICY_SET.md`.

**What:** Both files hash-match the Controller-stated values in the Release Command
(`03fdf634…d220` and `2a2bc0c2…d34` respectively — MATCH, measured). Their content records two
Human Owner ACTIVATE decisions: ENTRY-001 (C1/C2/C3, `2026-08-07T16:43:58+09:00`) and ENTRY-002
(C4, `2026-08-08T16:50:21+09:00`), each citing the same SHA256 values for C2/C3/C4 that this
Context independently re-measured against the `_AUTHORITY_RELEASE_EXACT` copy (7/7 MATCH,
including C4 = `cb4181f3…9ef`, identical to the Release Command's and the sealed expectation's
independent measurements).

**How found:** `sha256sum` over `_AUTHORITY_RELEASE_EXACT/**` compared against each file's
`.sha256` sidecar and against the Controller-stated values in the Release Command; then reading
the two activation-log entries in full.

**Resolution:** Under Reading A (C4 ACTIVE), which this evidence now supports directly rather
than only by the expectation's dual-reading fallback: **C4 is ACTIVE as of
2026-08-08T16:50:21+09:00**, well before this audit. C4 Article 33 T-1 binds. LBU-1 does not
remain open. It does not block.

**Residual, non-blocking:** the activation log is itself a document in the same disclosed copy;
this Context cannot certify from outside the copy that the log's own account of a Human Owner
decision is not itself fabricated. No evidence suggests it is. Recorded per M5 as a measurement
limit, not as a finding against the process.

---

## 2. LBU-2 (canonical provenance of the authority copy) — CARRIED, non-blocking

**Where:** `_AUTHORITY_RELEASE_EXACT/**` (9 files).

**What:** All 9 files hash-match their sidecars and match three independently-taken
measurements: the Release Command's Controller re-hash (post-fetch), the sealed Secondary
expectation's §1.3 measurement (taken before target disclosure), and the values embedded in
`ACTIVATION_DECISION_LOG.md` itself (taken at Activation time, 2026-08-07/08). All three
converge on identical SHA256 values for every document, including C4 (`cb4181f3…9ef`).

**How found:** `sha256sum` over `_AUTHORITY_RELEASE_EXACT/**`, cross-referenced against the three
cited sources above (all already disclosed/authenticated material).

**Assessment:** Convergence across three measurements taken at different times by different
Contexts is stronger evidence than self-consistency alone, but it is still evidence internal to
this platform's own record-keeping, not an external canonical source reachable from this Context.
LBU-2 is carried, not resolved. It is recorded as `LOAD_BEARING_UNKNOWN` per its original
definition (its answer would change the verdict if the copy were wrong), but no evidence of
divergence was found, so it does not by itself move the verdict off `PASS`-compatible ground.

---

## 3. T-1 — outbound transmission / third-party write (Article 33 T-1, expectation §3–§4)

**Where:** custody commits `ebacef95…f0bc1`, `4ec5e267…7a881d`, `e64dbbfe…9258392611f`,
`34fb1b2f…03dfc69` on `https://github.com/goltuchi55-gif/Rian_Claude_Controller.git`.

**What:** `git merge-base --is-ancestor <sha> origin/main` returns true for all four — each
commit is an accepted ancestor of the remote's `main` ref. `git remote get-url origin` shows the
remote is `https://github.com/goltuchi55-gif/Rian_Claude_Controller.git`, a GitHub-hosted,
third-party-operated service. The Secondary expectation §4 Q-3, itself sealed before target
disclosure and citing Phase Definition R-04's own concession that the repository must not
receive published source code, establishes the repository is public.

**How found:**
```
git remote get-url origin
git merge-base --is-ancestor <sha> origin/main   # exit 0 for all four
```

**Classification (§3 E-1/E-2):** bytes left the local machine and a ref advanced on storage this
platform does not own. This is outbound transmission and third-party write by effect, regardless
of the "custody"/"deposit" vocabulary used to describe it (E-3). Because the repository is
public, it is also publication (Q-3): the bytes are retrievable by unnamed parties and, given the
no-force-push/no-history-rewrite constraint (§S-below), not reliably retractable.

**Verdict on this finding:** T-1 = **FIRED, correctly classified as fired**. This is not itself a
FAIL: the process opened this very Secondary Audit under T-1 rather than denying it on naming
grounds, which is the Corollary in expectation §5 — evidence the trigger was honoured. Does not
block.

**Timing note (§5 A-3 Corollary, case (a) vs (b)):** the four commits' committer timestamps
(`2026-08-23T01:23:41` → `02:37:59` → `09:39:16` → `11:12:26`, all JST) show the pushes happened
progressively across the day, and the Secondary expectation (which formalizes T-1 recognition)
was sealed at `02:07:47`, i.e. **after** the first push (`ebacef95`, Primary expectation deposit,
`01:23:41`) but **before** the BUILD_READY and Primary-result pushes. Recognition of T-1 was
therefore not fully pre-flight for every one of the four deposits — the first deposit preceded
even the Secondary expectation's own sealing. This is `T-2`/`T-3`-adjacent process timing, not a
denial-on-naming-grounds FAIL, and is recorded as a residual, non-blocking process observation
per expectation §5 Corollary case (b): late recognition, not non-recognition.

---

## 4. S-1 — single emitter / custody-actor identity (expectation §6 S-1, S-3)

**Where:** git author/committer identity of the four named commits.

**What:** measured via safe metadata only (`git log --format="%an / %cn"`, no message/body read):

| commit | role in process | author = committer |
|---|---|---|
| `34fb1b2f…` (Secondary expectation deposit) | AUDITOR (secondary, self) | `RIAN_SECONDARY_AUDITOR` |
| `ebacef95…` (Primary expectation deposit) | — | `goltuchi55-gif` |
| `4ec5e267…` (BUILD_READY deposit) | IMPLEMENTER | `CLAUDE_A_IMPLEMENTER` |
| `e64dbbfe…` (Primary audit-result deposit) | — | `goltuchi55-gif` |

**How found:**
```
git log -1 --format="author=%an <%ae>  committer=%cn <%ce>" <sha>
```
run individually for each of the four SHAs (metadata only, permitted under the Release Command).

**Finding:** the BUILD_READY custody commit (`4ec5e267…`) is authored and committed under the
identity `CLAUDE_A_IMPLEMENTER` — the same label the IMPLEMENTER's own BUILD_READY result
document (`P0_5_001_IMPLEMENTATION_RESULT_R1_20260823.md`) uses for itself. Phase Definition
R-05 is described (by the sealed expectation, §3 E-3, itself read pre-seal from Phase Definition)
as separating the substantive worker from a distinct, named remote-push actor
(`LOCAL_CUSTODY_RELAY`). **No commit among the four named custody commits carries the identity
`LOCAL_CUSTODY_RELAY`, or any single consistent identity at all** — four commits, three distinct
author identities, none matching the declared relay label.

**Assessment against §6 S-1:** "Did the substantive IMPLEMENTER perform any remote push itself,
contrary to R-05?" cannot be answered NO from permitted evidence. The commit that reached the
public remote for the BUILD_READY artefact is labelled with the IMPLEMENTER's own identity, not
a separate custody component's. Git author/committer identity is a self-declared field (set by
whatever process ran the commit) and is not, on its own, proof that `CLAUDE_A_IMPLEMENTER` itself
executed `git push` rather than a distinct relay committing under a borrowed `user.name` — but
the burden under the sealed criteria runs the other way: §2.3 requires treating undecidability as
"present." The actual custody mechanism (`50_CUSTODY/`) is not in this stage's disclosed target
and could not be inspected.

**Classification:** `LOAD_BEARING_UNKNOWN`. This would change the verdict (single-emitter /
process-separation compliance under expectation §9 PASS-3 cannot be recorded as demonstrated).
**Blocks PASS; does not by itself justify FAIL** — no evidence of an actual R-05 violation was
found, only an absence of evidence that the declared separation held for the identity dimension.
Per §9 NEEDS_HUMAN, this is exactly a "boundary question genuinely undecidable on the evidence."

---

## 5. S-2 — envelope reconciliation for the four named commits (expectation §6 S-2)

**Where:** `git diff-tree --no-commit-id --name-only -r <sha>` for each of the four commits.

**What (measured):**

| commit | changed paths | all within one declared prefix? |
|---|---|---|
| `34fb1b2f…` | `05_EVIDENCE/P0_5-001/AUDIT/SECONDARY/EXPECTATION/CUSTODY_PENDING/*.md`, `*.sha256` | YES |
| `ebacef95…` | `05_EVIDENCE/P0_5-001/AUDIT/EXPECTATION/CUSTODY_PENDING/*.md`, `*.sha256` | YES |
| `4ec5e267…` | `05_EVIDENCE/P0_5-001/IMPLEMENTATION/BUILD_READY/*` (6 files) | YES |
| `e64dbbfe…` | `05_EVIDENCE/P0_5-001/AUDIT/RESULT/*.md`, `*.sha256` | YES |

Each commit is single-parent (`git rev-list --parents -n 1 <sha>` — no merge commits), touches
exactly one evidence prefix, and pairs every `.md`/`.tsv` with its `.sha256` sidecar. No commit's
changed-path set crosses into another prefix or touches an unrelated path.

**Finding:** for these four specific events, declared-envelope compliance IS measured (not merely
asserted) and holds. **Does not block; PASS on this sub-criterion for the four named commits.**
This does not extend to the full custody mechanism generally (see §7 below).

---

## 6. S-4 — byte integrity across the boundary (expectation §6 S-4)

**Where:** `05_EVIDENCE/P0_5-001/IMPLEMENTATION/BUILD_READY/*`, `_AUTHORITY_RELEASE_EXACT/*`,
`05_EVIDENCE/P0_5-001/AUDIT/SECONDARY/EXPECTATION/CUSTODY_PENDING/*`.

**What:** every artefact this Context could read had its SHA256 independently recomputed and
compared: 9/9 authority documents MATCH; the Secondary expectation and its sidecar MATCH each
other and MATCH the Release Command's cited value; `P0_5_001_IMPLEMENTATION_RESULT_R1…md`,
`P0_5_001_BUILD_MANIFEST_R1.tsv`, and their sidecars all MATCH the values declared in
`P0_5_001_BUILD_READY_IDENTITY_SUMMARY_R1_20260823.md`.

**How found:** `sha256sum <file>` compared against `<file>.sha256` and against
Controller/prior-stage-cited values, for every readable artefact.

**Finding:** byte integrity is demonstrated, not asserted, for every artefact in scope.
**Does not block.**

**Also measured:** `git config --local --get core.autocrlf` and `--global --get core.autocrlf`
both return empty (unset) in this workspace; the deposited `.gitattributes` under
`BUILD_READY/` (`* text eol=lf`) is scoped to that one directory and does not touch the repo
root. Consistent with the no-global-config-mutation requirement (R-06 / S-4). Non-blocking.

---

## 7. S-1/S-3/S-5/S-6 — custody mechanism itself is out of this stage's disclosed target

**Where:** `50_CUSTODY/` (referenced by `envelope.py`'s `CUSTODY_ROOT` constant and by the
BUILD_READY result's WRITE_ENVELOPE table) is not part of the Release Command's disclosed
target for this stage, and no directory of that name is materialized in this Context's sparse
checkout.

**What:** this Context can verify that the IMPLEMENTER's own write-isolation code
(`10_IMPLEMENTER/src/p05/envelope.py`) is real, substantive, fail-closed logic (absolute-root
allowlist, resolved once at construction, denial on ambiguity/traversal/UNC/device paths/
reserved names) rather than an assertion — and that this logic only governs the
`10_IMPLEMENTER` root, not the remote-push mechanism. It cannot verify from the disclosed
target whether the actual custody/push process (a) is a single deterministic component, (b)
made no discretionary selection, or (c) touched any unrelated worktree, because that
mechanism's source is not disclosed at this stage.

**How found:** `Read` of `envelope.py`; `Glob` over the disclosed target confirming absence of
any `50_CUSTODY` or push-script material.

**Classification:** `UNKNOWN`, non-adverse (no evidence of a violation, only absence of the
material needed to measure S-3/S-5/S-6 for the remote-push mechanism itself). Combined with the
§4 S-1 identity finding, this is folded into the same `LOAD_BEARING_UNKNOWN` — the custody
mechanism's separation and discretion-free operation cannot be measured from what this stage
disclosed.

---

## 8. T-5 — restore route (expectation §4 Q-5, §9bis)

**Where:** `P0_5_001_IMPLEMENTATION_RESULT_R1_20260823.md` §ROLLBACK;
`P0_5_001_BUILD_READY_IDENTITY_SUMMARY_R1_20260823.md` §CUSTODY CONDITIONS.

**What:** the only stated restore route in any disclosed document is local:
`Remove-Item -Recurse -Force '...\10_IMPLEMENTER\*'` (and `rollback.cmd`), explicitly scoped to
the pre-push local build directory. No document in the disclosed target states a restore route
for the bytes already pushed to the public remote (the four accepted, non-force-pushable
commits). The custody conditions explicitly commit to "no force-push and no history rewrite,"
which by design makes the pushed bytes non-retractable through the remote itself.

**How found:** reading the ROLLBACK and CUSTODY CONDITIONS sections of the two disclosed
BUILD_READY documents; cross-checked against `git merge-base --is-ancestor` confirming all four
commits are currently accepted ancestors of `origin/main` with no evidence of any subsequent
revert/force-push in the visible ref history.

**Finding:** T-5 fires — a restore route for the remote-reaching effect cannot be stated in one
line from any disclosed evidence. This matches the sealed expectation's own pre-registered
candidate observation (§9bis). **`LOAD_BEARING_UNKNOWN`-adjacent but resolves to a direct
finding**, not an unknown: the absence is measured, not inferred from silence (M5) — the two
documents that would be expected to state a remote restore route were read in full and do not
contain one. Does not on its own justify FAIL (M3's requirement is a named, confirmed rollback
route before a change *starts*; whether one existed contemporaneously but is simply not recorded
in the disclosed evidence is itself the undecidable question). Contributes to `NEEDS_HUMAN`.

---

## 9. G-1 through G-6 boundary checks

- **G-1 (production status of the repository):** no canon document naming this repository's
  production status was in the disclosed target. Fail-closed default per `CONSTITUTION_LITE` M3
  is to treat silence as production. **`LOAD_BEARING_UNKNOWN`** — not resolved by this stage's
  disclosure.
- **G-2 (deploy test):** no evidence any running system reads from
  `goltuchi55-gif/Rian_Claude_Controller.git`; disclosed evidence describes it only as an
  evidence/handoff deposit target. **No adverse finding measured; residual UNKNOWN,
  non-blocking** under G-2 specifically (independent of G-1).
- **G-3 (credential boundary):** BUILD_READY result states credential-shaped environment
  variables are stripped from the worker's child environment and asserts no credential was
  read/created/modified/revoked/logged; this is IMPLEMENTER self-report, not independently
  re-executed by this audit. A `git push` to an HTTPS remote necessarily used *some* ambient
  credential (use, not change) — consistent with M4's use/change distinction. **No adverse
  finding measured; residual UNKNOWN on independent re-verification, non-blocking.**
- **G-4 (financial boundary):** no evidence of any write reaching money-moving/order-executing
  software; `10_IMPLEMENTER` tree contains no such component. **Not observed; non-blocking.**
- **G-5 (canonical boundary):** `_AUTHORITY_RELEASE_EXACT/**` was read-only in this Context
  (no write tool was ever invoked against it); no canonical document's content was modified by
  this audit. **Not observed; non-blocking.**
- **G-6 (live model request):** `P0_5_001_IMPLEMENTATION_RESULT_R1…md` §HEADLESS_CLAUDE_FEASIBILITY
  states only `--version`/`--help` were invoked, enforced by a closed argv-tail allowlist in
  `headless_probe.py` (not independently re-read by this Context beyond the result document's
  description). **Not observed; non-blocking**, with the same self-report caveat as G-3.

---

## 10. D-3 hygiene (this Context's own)

**What was read before this RAW was fixed:** the Release Command, the sealed Secondary
expectation, the `_AUTHORITY_RELEASE_EXACT` snapshot (full), `10_IMPLEMENTER/src/p05/envelope.py`,
the three `BUILD_READY` documents in full, safe git metadata (existence, ancestry, remote URL,
`diff-tree --name-only`, author/committer identity, commit dates, parent counts) for the four
named commits only.

**What was NOT read:** `05_EVIDENCE/P0_5-001/AUDIT/RESULT/**` content beyond its changed-path
list (never opened — the directory is not materialized in this sparse checkout); any Primary
AUDITOR finding body, grounds, verdict or reasoning; any commit message or blob content of
`ebacef95…` or `e64dbbfe…`; `00_CONTROL/P0_5-001/P0_5_001_CONTROLLER_T1_DETERMINATION…` or
`00_CONTROL/CURRENT_STATUS.md` (neither is materialized in this checkout — confirmed absent by
`Glob`); any P0-C audit body; `git log`/`git show`/`git diff`/`blame` on commit content (only
`git log --format` restricted to hash/date/author/committer fields, and `diff-tree --name-only`,
were run).

**Finding:** `D3_HYGIENE = PASS`. No contamination occurred.

---

## Summary of findings by disposition

| id | statement | classification | blocks? |
|---|---|---|---|
| F-1 | LBU-1 resolved: C4 ACTIVE since 2026-08-08T16:50:21+09:00 | resolved, favorable | no |
| F-2 | LBU-2 carried: authority-copy provenance not externally provable, but 3-way convergent | LOAD_BEARING_UNKNOWN | contributes to NEEDS_HUMAN |
| F-3 | T-1 fired (public third-party push, accepted); honoured by opening this audit | confirmed, non-adverse | no |
| F-4 | T-1 recognition was not fully pre-flight for the first of four deposits | residual, non-blocking | no |
| F-5 | S-1: no commit among the four carries the declared custody-relay identity; BUILD_READY commit carries the IMPLEMENTER's own identity | LOAD_BEARING_UNKNOWN | contributes to NEEDS_HUMAN |
| F-6 | S-2: envelope reconciliation measured and holds for all four named commits | confirmed, favorable | no |
| F-7 | S-4: byte integrity demonstrated for every readable artefact | confirmed, favorable | no |
| F-8 | S-3/S-5/S-6: custody mechanism (`50_CUSTODY/`) not disclosed at this stage; cannot be measured | UNKNOWN, non-adverse | folds into F-5 |
| F-9 | T-5: no one-line restore route stated anywhere in disclosed evidence for the already-pushed public bytes | measured absence | contributes to NEEDS_HUMAN |
| F-10 | G-1: repository's production status not named in any disclosed canon document | LOAD_BEARING_UNKNOWN | contributes to NEEDS_HUMAN |
| F-11 | G-3/G-6: credential and live-model-request claims are IMPLEMENTER self-report, not independently re-executed | residual, non-blocking | no |

BLOCKING_FINDINGS (findings that on their own would compel FAIL): **0**.
LOAD_BEARING_UNKNOWN (would change the verdict, unresolved): **F-2, F-5, F-9, F-10 = 4**.
OPEN_MUST (confirmed unmet canonical requirement): **0**.

*End of RAW findings. Fixed and not to be altered after this point.*
