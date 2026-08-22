---
document_id: P0C_001_PRIMARY_AUDIT_VERDICT_R2
document_type: PRIMARY_AUDIT_SUPPLEMENTAL_VERDICT
change_id: P0C-001
auditor: CLAUDE_B / C4_ROLE=AUDITOR / ORDER=PRIMARY
issued_under: P0C_001_CURRENT_COMMAND_R5 (1fae6bca…3bae40)
issued_at_jst: 2026-08-22
verdict: PASS
open_must: 0
load_bearing_unknown: 0
blocking_findings: 0
secondary_audit_required: NO
basis_status: RESOLVED_AGAINST_AUTHORIZED_CANONICAL_COPY
supplements: P0C_001_PRIMARY_AUDIT_VERDICT_R1_20260822.md
supersedes: NOTHING
---

# P0C-001 Primary Audit — Supplemental Verdict R2

This verdict supplements Verdict R1. It does **not** replace it, repair it, or rewrite it. R1 and the
RAW findings remain immutable history and remain the record of what was knowable at the time they were
sealed. R2 re-evaluates **only** the basis-dependent portion of R1, as R5 directs.

| artefact | SHA-256 | state |
|---|---|---|
| `P0C_001_PRIMARY_AUDIT_EXPECTATION_R1_20260822.md` | `fc473adc…6976` | unchanged |
| `P0C_001_PRIMARY_AUDIT_RAW_FINDINGS_R1_20260822.md` | `75a658e3…abd1` | unchanged |
| `P0C_001_PRIMARY_AUDIT_VERDICT_R1_20260822.md` | `d7681947…b35c` | unchanged |
| audit target | `2eb3cc51…7d00` | unchanged, re-measured |

## Verdict

**`PASS`** — `OPEN_MUST = 0`, `LOAD_BEARING_UNKNOWN = 0`, `BLOCKING_FINDINGS = 0`.

## What changed, and what did not

R1 returned `NEEDS_HUMAN` for exactly one reason: the sealed expectation prohibits a PASS under basis
ambiguity, and my canon basis was a copy its own notice declares `NON_CANONICAL`, whose
`ACTIVE_POLICY_SET` match was self-referential. Nothing about the candidate caused that verdict — R1
already recorded zero blocking findings in it.

R5 directed me to a pre-existing Human-issued R8 decision I had not located. It authenticates, and it
resolves the ambiguity. **No new information about the candidate was produced, and no finding was
withdrawn.** The candidate is exactly as good, and exactly as flawed, as R1 found it.

## Basis resolution — what was measured

Full record in `P0C_001_PRIMARY_AUDIT_BASIS_EVIDENCE_R2.tsv` (15 rows, all MEASURED).

**R8 Human authority — AUTHENTICATED.** All three expected identities reproduce exactly:
Directive `6dda7394…b256`, Approval `8c4dc1ae…7518`, custody manifest `e989a813…f5fb`. The approval
carries `document_status: HUMAN_ISSUED_APPROVAL`, `decision: APPROVED_WITH_CONDITIONS`, and
`APPROVED_BY: I CONFIRM THIS HUMAN DECISION`; it explicitly supersedes the unsealed R1–R7 candidates.
It is an issued artefact, not a pending one — the fail-closed condition in R5 item 3 does not trigger.

Its text carries the claimed authority verbatim: `D1_C1…C4_AUTHORITY: AUTHORIZED_CANONICAL_COPY_VIA_GIT`,
`D1_OPERATING_PROFILE_AUTHORITY: INCLUDED_IN_C1_AUTHORIZED`, `D1_CANONICAL_AUTHORITY_STATUS: RESOLVED`,
conditioned on `MEASURED_SHA256_MATCHES_ACTIVATED_CANONICAL_IDENTITY`, with
`AUTHORIZATION_LAPSES_ON_DIGEST_DIVERGENCE: TRUE`, and with the Git copy explicitly **not** a second
canonical writer and granted no modify / activate / supersede authority.

**Activated canonical identity — 9/9 EXACT, 0 divergence.** I re-measured every document in the
activated set (C1 x6, C2, C3, C4) against the identities recorded at activation. All nine reproduce
byte-exactly. R8's authorization condition is therefore satisfied and its lapse clause does not fire.

**Independent structural cross-check.** R8 states `c1_layer_document_count: 6`,
`c1_named_load_bearing_count: 2`, `c1_remaining_document_count: 4`, naming the four. The copy contains
exactly six C1 documents and exactly those four names. This matters: it is a description of the copy
written in an artefact held *outside* the copy, and it matches. That is what breaks the circularity
R1 could not break — an external Human artefact both designating the copy as governing and
independently describing its composition.

## Residual, stated precisely rather than dissolved

R8 does not enumerate the nine digests itself; the activated identity list is still read from
`ACTIVE_POLICY_SET` inside the authorized copy. So this is not a second independent digest source.
What closed the gap is that a Human decision external to the copy designates it as the authorized
governing read/use copy — which makes reading the activated list from it the authorized act, not a
circular one. `C:\Projects\Claude_Development_Platform_Lite` remains absent, which R5 item 5 correctly
directs is not by itself an authority failure.

Two limitations a reader should weigh:

1. **Cross-change reliance.** R8 was issued under `change_id: CTRL-AUTO-HANDOFF-002`, not P0C-001. I
   accept it because its D1 block is a determination of *which copy of canon governs* — inherently not
   change-scoped, marked `RESOLVED`, and carried forward unchanged from R7 as a standing
   determination. R8 was issued 2026-08-21T20:02:25 and the P0-C work followed it, so
   `retroactive_authorization: FALSE` is not offended. A reader who rejects cross-change reliance
   should read this verdict as R1 instead.
2. **Correlated failure, unchanged.** The limitation in R1 §6 stands in full. Lineage independence was
   never achieved, `OI-4` is unmitigated, and HQ-G defers the different-lineage Auditor question. A
   basis resolution does not touch this.

## Findings — all seven preserved as findings

The six NON-BLOCKING findings in the RAW record are preserved exactly and are **not** repaired,
withdrawn, or downgraded by this verdict: F-01 (GAMMA sealed `COMPLETE` before its required audit),
F-02 (BETA status outside the canonical five-state list), F-03 (identity table missing a digest),
F-04 (HQ-C/HQ-E approve a proposition their source did not ask), F-05 (`LOAD_BEARING_UNKNOWN=0` is a
redefined metric), F-06 (PRE-1 proposed while operations already run against it).

One new NON-BLOCKING finding arises from the basis resolution itself:

### F-07 — an existing Human authority was not located, and the packet understates its own basis — NON-BLOCKING

**Where:** candidate `canonical_citation_status: PROVISIONAL_AGAINST_REFERENCE_COPY`; section 0
canonical limitation; section 9 `UNKNOWN-G1` marked OPEN and implementation-blocking.

**Defect:** the R8 Human decision resolving canonical authority for the Git copy was issued
2026-08-21T20:02:25, **before** the P0-C groups sealed on 2026-08-22. Neither the groups, nor the
Controller integration, nor the governance tier verification located it. The packet therefore carries
its canonical citations as provisional and `UNKNOWN-G1` as implementation-blocking when a standing
Human authority already covered the point.

**How found:** authenticated R8 under R5, then compared its issuance timestamp against the group seal
and integration timestamps.

**Blocking:** no — and the error runs in the safe direction. Treating available authority as absent is
fail-closed; the reverse would have been a defect worth blocking on. Recorded because `UNKNOWN-G1` is
cited across the packet as an implementation blocker and, on this evidence, its premise no longer
holds.

## C4 Article 33 — re-evaluated

T-1 through T-5 all remain **NOT MET**. `SECONDARY_AUDIT_REQUIRED = NO`. This verdict is not itself a
trigger. A dispute over a finding (T-2) or a challenge to a measurement in it (T-3) would establish
one, and any Secondary Auditor must be a new Context that does not read R1, R2, or the RAW body before
fixing its own RAW result.

## Authority

This verdict grants nothing. It is not a Human Gate, not an approval of the candidate, not
implementation authority, and not canon promotion. It authenticates an existing Human decision; it
does not create one. The Human Owner's decision on HQ-A…HQ-I remains outstanding and must be issued as
a separate artefact in `00_HUMAN\` binding this candidate's exact SHA-256.
