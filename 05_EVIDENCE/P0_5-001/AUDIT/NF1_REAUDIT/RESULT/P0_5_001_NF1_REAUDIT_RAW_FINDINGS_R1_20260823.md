---
document_id: P0_5_001_NF1_REAUDIT_RAW_FINDINGS_R1
document_type: AUDIT_RAW_FINDINGS
revision: 1
change_id: P0_5-001
phase: P0.5
finding_id: NF-1
c4_role: AUDITOR
order: secondary
scope: process
stage: result
authored_by: FRESH_GRBETA_R1_C4_AUDITOR
authored_at_jst: 2026-08-23T13:15:00+09:00
expectation_ref: 05_EVIDENCE/P0_5-001/AUDIT/NF1_REAUDIT/EXPECTATION/P0_5_001_NF1_REAUDIT_EXPECTATION_R1_20260823.md
expectation_sha256: e62d6d98ea2ea9749a433361d8fec683f8e804412ec1b51a0e9a377805441a64
status: IMMUTABLE
---

# P0.5-001 NF-1 Re-Audit RAW Findings R1

This RAW result was fixed against the criteria sealed in the expectation referenced above, sealed and
committed before the target Human Decision body was opened. Once written this file is immutable.

## MEASURED CHECKS (against sealed criteria C-1..C-8)

### C-1 — Repo HEAD identity at start of session
Measured: `git rev-parse HEAD` = `b2162b693ddfcf8d6e1c697eee709947b7549a0a` (confirmed at session
start, before any of my own artifacts existed). Matches the commit identity given for the target.
**RESULT: PASS.**

### C-2 — Byte identity of target
Measured: `sha256sum 00_HUMAN/P0_5-001/P0_5_001_HUMAN_DECISION_NF1_CUSTODY_PATH_R1_20260823.md` =
`3f0d5ebc1ec54bb9e1cf8659043f66fd867631ca757be7a576edb266e6707eb0`. Sidecar file content is the
identical value. Both equal the claimed target SHA256 given to me before expectation. **RESULT: PASS.**

### C-3 — Commit scope
Measured: `git show --stat b2162b693ddfcf8d6e1c697eee709947b7549a0a` touches exactly two paths:
`00_HUMAN/P0_5-001/P0_5_001_HUMAN_DECISION_NF1_CUSTODY_PATH_R1_20260823.md` and its `.sha256` sidecar.
No other path, no canon text, no runtime/production file. **RESULT: PASS.**

### C-4 — Path authorization / no scope extension
Measured by reading the target body (first read, post-seal). The DECISION section approves
`00_HUMAN/P0_5-001/` solely as custody for "Human Decision本体およびdetached SHA256 sidecar" (the Human
Decision artifact itself and its detached SHA256 sidecar) — this matches the audited question exactly.
The "NOT AUTHORIZED BY THIS DECISION" section explicitly excludes: implementation source, runtime
state, credential/secret, Production deploy, trading/financial execution, and general-purpose remote
write path. No open-ended or "as needed"/"related path" language is present anywhere in the body.
**RESULT: PASS.**

### C-5 — No auto-extension
Measured: the body contains an explicit "NON-EXTENSION RULE" section stating this custody-path pattern
must not auto-extend to a new phase/change, and that the decision is limited to `change_id: P0_5-001`.
The frontmatter also carries `change_id: P0_5-001` as structured data, not prose. No language in the
body grants new authority, actor, or write envelope beyond the custody-path question asked.
**RESULT: PASS.**

### C-6 — Preservation of existing evidence
Measured: (a) commit scope check (C-3) shows no prior evidence file touched by the target commit; (b)
the target body's own "PRESERVATION / EFFECT BOUNDARY" section states existing
`P0_5_001_CONTROLLER_PHASE_DEFINITION_R1`, existing Evidence, and existing audit RAW/Verdict artifacts
(explicitly naming `P0_5_001_HUMAN_RESOLUTION_CLOSURE_AUDIT_VERDICT_R1` as remaining immutable) are
unchanged by this decision; (c) I independently cross-checked, by SHA256 only (no content read), that
`05_EVIDENCE/P0_5-001/AUDIT/HUMAN_RESOLUTION_CLOSURE/RESULT/P0_5_001_HUMAN_RESOLUTION_CLOSURE_AUDIT_VERDICT_R1_20260823.md`
hashes to `716cf281812d33515ef6935c94e7af652340307a3ebc4f4c595a096d0b98a2bf`, matching both its own
sidecar and the `resolves_audit_sha256` value declared in the target's frontmatter — the referenced
prior verdict is byte-identical to what the target claims it references, and unread beyond its hash.
(d) my own re-audit deposit (expectation, this RAW, and the forthcoming verdict) is additive-only under
a new `05_EVIDENCE/P0_5-001/AUDIT/NF1_REAUDIT/` subtree. **RESULT: PASS.**

### C-7 — NF-1 closure status
Measured: the target body's "SCOPE OF EFFECT ON NF-1" section states this decision corresponds to
"option 1" of the closure audit's presented options (confirming `00_HUMAN/P0_5-001/` as the authorized
P0.5 custody path) and explicitly does not amend `P0_5_001_CONTROLLER_PHASE_DEFINITION_R1` R-04's
enumerated list ("option 2" is not taken). The same section states in plain text that "本artifact自体は
NF-1のcloseを宣言しない" — this artifact itself does not declare NF-1 closed; it reserves the closure
determination to the Controller. The underlying custody-path question is answered unambiguously and
in-scope; formal closure of the finding record is a Controller act, not self-declared by the Human
Decision. This is consistent with the canon's role separation (Human Owner decides, Controller records
state) and is not treated as a defect. **RESULT: substantive question RESOLVED; formal NF-1 closure
declaration is a Controller action outside this artifact and outside a re-audit's authority to perform.**

### C-8 — Non-waivable boundaries (M1/M3/M4)
Measured: the target's "NON-AUTHORIZATION RESTATEMENT" section explicitly excludes Production
operation, credential/secret change, financial/trading/order execution, force-push, history rewrite,
and canonical C1-C4 text modification. The commit itself (C-3) touches only the two custody files.
No M1/M3/M4-class element is present. **RESULT: PASS.**

## OUT-OF-SCOPE ITEMS NOTED BUT NOT ADJUDICATED

The target's frontmatter references `resolves_audit: P0_5_001_HUMAN_RESOLUTION_CLOSURE_AUDIT_VERDICT_R1`,
whose historical verdict on F-2/F-5/F-9/F-10 was `NEEDS_HUMAN` (identity confirmed by SHA cross-check
only, per C-6). This re-audit's sealed scope is NF-1 only. Whether F-2/F-5/F-9/F-10 are themselves
separately resolved is not evaluated here, per this audit's own no-auto-extension rule (Section 6 of the
expectation) and per D-3 (that reasoning was not read before this RAW was fixed).

## AGGREGATE COUNTS

- OPEN_MUST = 0 (measured: all of C-1..C-8 pass; no MUST-class defect found)
- LOAD_BEARING_UNKNOWN = 0 (measured: no criterion required Human adjudication; C-7's Controller-action
  point is a role-separation fact, not an UNKNOWN)
- BLOCKING_FINDINGS = 0 (measured: no Section-3 FAIL condition from the sealed expectation was
  triggered)

## D-3 HYGIENE

No prior Primary Audit, Secondary Audit, Human Resolution Closure Audit RAW/verdict body, grounds, or
reasoning content was read before this RAW was fixed. The only prior-audit material touched was: (a)
COMMAND documents (permitted, cross boundary by design), (b) git commit metadata (subject/author/path
lists only), (c) one detached SHA256 cross-check of the Human Resolution Closure Audit Verdict file's
bytes, performed without opening or reading its content, solely to verify the target's own
`resolves_audit_sha256` claim. **D3_HYGIENE: PASS.**
