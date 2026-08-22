---
document_id: P0C_001_PRIMARY_AUDIT_RAW_FINDINGS_R1
document_type: PRIMARY_AUDIT_RAW_FINDINGS
change_id: P0C-001
auditor: CLAUDE_B / C4_ROLE=AUDITOR / ORDER=PRIMARY
executed_under: P0C_001_CURRENT_COMMAND_R2 (via R3 item 3)
issued_at_jst: 2026-08-22
status: RAW_IMMUTABLE
basis_status: PROVISIONAL_AGAINST_REFERENCE_COPY
---

# P0C-001 Primary Audit — RAW Findings

RAW. Not to be replaced by the verdict summary, repaired, or rewritten.

## 0. Provenance statement

No previously completed Primary Audit result existed in the P0-C audit workspace, anywhere in the
change root, or on `origin/main` when this context ran. `P0C_001_AUDITOR_HANDOFF_BOOTSTRAP_R4`
assumed one existed. This document is a **fresh execution of R2 by this context** under R3 item 3
("If R2 did not actually finish creating the written result, finish R2 exactly as previously
commanded"). It is not a recovery, reconstruction, or transcription of any prior result.

## 1. Target identity — PASS

| field | value |
|---|---|
| target | `50_RIAN_CONTROLL\P0C_001_CONSOLIDATED_HUMAN_DECISION_CANDIDATE_R1_20260822.md` |
| expected (dispatch section 1) | `2eb3cc51f03bc5296f2630a22317d721807cce290392357607111877d56b7d00` |
| detached sidecar | identical |
| measured by auditor | identical |

Three-way match. The body was opened only after this, and only after the Controller Seal ACK
(`EXPECTATION_SEAL_CUSTODY = PASS`) released the disclosure gate.

## 2. Verified — reproduced, not accepted on narrative

| # | claim | method | result |
|---|---|---|---|
| V-1 | 9 HQ source rows quoted faithfully | byte-diff of candidate section 1 quotes vs `07_OPEN_QUESTIONS.md` lines 16-24 | **verbatim 9/9, zero diff** |
| V-2 | all 15 Master section 8 required contents present | mapped each to candidate sections 1-13 | 15/15 present |
| V-3 | each HQ-A…I carries one explicit decision row | read section 2 | 9/9 present |
| V-4 | group package digests in section 0 | recomputed all three | 3/3 match |
| V-5 | IV-002 `17/17 MATCH` | re-parsed all 64-hex manifest entries, recomputed named siblings | **17/17, independently reproduced** |
| V-6 | IV-001 `25/25 MATCH` | recomputed every `*.sha256` under the four scoped directories | 29/29 match today; 29 = 25 + the 4 sidecars created after the TSV's stated scope (candidate, controller manifest, workspace, audit dispatch). Reproducible. |
| V-7 | UNKNOWN-G1 not converted to PASS | read sections 0 and 9 | held OPEN and stated to block implementation |
| V-8 | no pre-filled GO / signature / approval value | read whole target | none present; the preamble explicitly forbids it |
| V-9 | one-correction-cycle limit respected | read three frontmatters | `correction_cycles_used: 1` in all three |

## 3. Findings

### F-01 — GAMMA completion state `COMPLETE` is not supportable — NON-BLOCKING

**Where:** `30_GAMMA\GAMMA_FINAL_SYNC_PACKAGE.md` frontmatter `status: COMPLETE`; propagated verbatim
into candidate section 0 input table.

**Defect:** `OPERATING_PROFILE_LITE` section 5 defines `COMPLETE` as "Done, verified, and **the review
its tier required has been done**." The tier is Full audit. At seal time no Independent Audit had
occurred — the candidate's own frontmatter says `independent_audit_status: PENDING`. GR_ALPHA, in the
identical situation, correctly used `DONE_PENDING_REVIEW`.

**How found:** compared all three sealed frontmatters against the closed five-state list in section 5.

**Blocking:** no. It changes no HQ decision. Reported because "COMPLETE" carried into an integration
table can later be misread as "audit done."

### F-02 — BETA completion state outside the canonical closed list — NON-BLOCKING

**Where:** `20_BETA\BETA_FINAL_SYNC_PACKAGE.md` frontmatter `status: SEALED_CANDIDATE_NOT_APPROVED`.

**Defect:** `OPERATING_PROFILE_LITE` section 5 is a closed list of five states ("Every session ends in
exactly one. If none of the others fits, use `PAUSED_SAFE`"). `SEALED_CANDIDATE_NOT_APPROVED` is not
among them. Secondary: BETA's frontmatter omits `open_must` and `load_bearing_unknown`, which ALPHA
and GAMMA both expose; BETA's values appear only in body prose.

**How found:** same comparison as F-01.

**Blocking:** no.

### F-03 — identity table carries a non-identity value — NON-BLOCKING

**Where:** candidate section 0, row `P0C_001_GOVERNANCE_TIER_VERIFICATION_R1_20260822.md`, SHA-256 column.

**Defect:** the column contains the literal words "detached sidecar" while the other three rows carry
64-hex digests. An identity table row without an identity.

**How found:** read section 0; recomputed the absent value, which exists and verifies against its
sidecar: `0b4e4585c12b32da35e8a6cafc5bd3a551ff17cd7c33b49ffaff61cd19a4c2c7`.

**Blocking:** no — the value is recoverable and correct. The defect is the omission.

### F-04 — HQ-C and HQ-E approve a proposition the source question did not ask — NON-BLOCKING, MATERIAL

**Where:** candidate section 2, rows C and E.

**Defect:** HQ-C's source question asks **only** where the signing key is placed (four location
options). The row returns `APPROVE custody boundary` — a proposition the source did not put — and
defers the question actually asked. HQ-E's source asks whether Evidence custody may move to the API
side (allow / disallow / conditional); the row approves a hybrid custody contract and defers the asked
proposition. A reader scanning the decision column sees "APPROVE" on both.

**How found:** compared each section 2 row against its verbatim section 1 source row.

**Blocking:** no — section 3 discloses the layering explicitly, which mitigates it. Reported because
the mitigation lives in a different section from the word "APPROVE."

### F-05 — `LOAD_BEARING_UNKNOWN=0` is a redefined metric — NON-BLOCKING, MATERIAL

**Where:** all three group terminal returns; candidate section 9 closing paragraph.

**Defect:** all three groups return `0` while ALPHA states "nine registered… all nine remain open,"
BETA states "six unknowns remain open," and UNKNOWN-G1 is stated to block implementation. The metric
means decision-sensitivity, not absence. The Master section 5 terminal contract used the bare term.

**How found:** read the three terminal blocks against candidate section 9.

**Blocking:** no — the redefinition is disclosed consistently in all four places, so this is a stated
convention rather than concealment. Reported because a downstream reader of the terminal line alone
would draw the wrong conclusion.

### F-06 — PRE-1 is proposed while operations already run against it — NON-BLOCKING, OBSERVATIONAL

**Where:** candidate section 7 push contract, PRE-1.

**Defect:** PRE-1 proposes that repo creation, remote config and first push not begin until
UNKNOWN-G1 closure or a separate Human decision explicitly naming the gap. UNKNOWN-G1 is OPEN, and the
active command chain (R1 item 9, R2 item 10, R3, R4) directs pushes to
`goltuchi55-gif/Rian_Claude_Controller` under `human_authority: P0C-001_HANDOFF_GIT_WRITE_APPROVED_20260822`.

**How found:** read section 7 against the authenticated command chain.

**Blocking:** no. The candidate is unapproved, so PRE-1 is not yet binding, and the repository
pre-exists with history so "first push" is already past. Surfaced so the Human sees that the packet
proposes a precondition the surrounding operation is already outside of.

## 4. UNKNOWN findings

| id | status |
|---|---|
| `UNKNOWN-G1` | **OPEN, and load-bearing on this audit.** Independently confirmed: `C:\Projects\Claude_Development_Platform_Lite` does not exist on this machine. A search across `C:\Projects`, `C:\Temp`, Desktop and Documents located no ACTIVE canonical root. My C4 and OPERATING_PROFILE basis is the Git reference copy, digest-matched to the `ACTIVE_POLICY_SET` record — but that record sits inside the same non-canonical copy, so the match is self-referential. |
| all residuals in candidate section 9 | inspected; each carries a fail-closed branch or a deferral. Not independently re-derived. |

## 5. C4 Article 33 trigger status — re-evaluated after the audit

| trigger | status |
|---|---|
| T-1 production / external send / money / third-party write / credential change | **NOT MET** — unchanged from the sealed expectation |
| T-2 Implementer disputed a finding | **NOT MET** — no dispute has occurred |
| T-3 the audit's own measurements were doubted | **NOT MET** — not raised |
| T-4 Human Owner requested | **NOT MET** — not issued |
| T-5 restore route not stateable in one line | **NOT MET** — unchanged |

`SECONDARY_AUDIT_REQUIRED = NO`.

## 6. Correlated-failure limitation

This Auditor shares model lineage with the producing contexts. Context independence was preserved —
the expectation was sealed before disclosure and custody-acknowledged by the Controller at
`fc473adc…6976` — but shared-lineage blind spots are not removed by context independence. This is the
candidate's own `OI-4`, rated MEDIUM, and it applies to this audit as much as to the work audited.
`UNKNOWN-A7 / B4` (different-lineage Auditor) is deferred at HQ-G, so no mitigation was available.
