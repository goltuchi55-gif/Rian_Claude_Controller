---
document_id: P0_5_001_PRIMARY_AUDIT_VERDICT_R1
document_type: PRIMARY_AUDIT_VERDICT
change_id: P0_5-001
phase: P0.5
auditor: CLAUDE_B / C4_ROLE=AUDITOR / ORDER=PRIMARY
issued_under: P0_5_001_FULL_AUDIT_RELEASE_COMMAND_R1 (4f06646f…306e)
issued_at_jst: 2026-08-23
verdict: PASS
open_must: 0
load_bearing_unknown: 0
blocking_findings: 0
secondary_audit_required: NO
judged_against: P0_5_001_AUDIT_EXPECTATION_R1_20260823.md (a5a46fda…928b)
raw_findings: P0_5_001_PRIMARY_AUDIT_RAW_FINDINGS_R1_20260823.md
---

# P0.5-001 Primary Audit — Verdict

This verdict does not replace the RAW findings. It enumerates every BLOCKING finding in full and states
the ground of the verdict. The sealed expectation was the judgment criteria and was not edited,
softened, or reinterpreted after disclosure.

## Verdict

**`PASS`** — `OPEN_MUST = 0`, `LOAD_BEARING_UNKNOWN = 0`, `BLOCKING_FINDINGS = 0`.

## BLOCKING findings

**None.**

## Why PASS is warranted

I re-measured the load-bearing claims rather than accepting them. The 84-test suite reproduced under my
own invocation with zero failures. The build manifest matched actual bytes 29/29 at audit start and
again 29/29 at audit end, so the target did not move underneath the audit. No network capability exists
anywhere in the package. Prompt submission is structurally impossible, not merely undone: the headless
probe's argument allowlist is a closed two-tuple with a refusal exception and `DEVNULL` stdin. SHA
authentication provably precedes worker launch. Blind resend is refused both after a terminal state and
while an outcome is unknown. No source code, secret or credential reached the public repository, and
every deposit stayed inside the authorized P0.5 paths.

The single most persuasive item was not planned by either side. To avoid disturbing the audited tree I
copied the whole build to a scratch path and ran it there — and the write envelope **denied its own
test suite** with `OUTSIDE_ALLOWLIST`. A relocated copy could not write, because the allowlist is bound
to resolved absolute paths and fails closed on anything it has not been told about. That is containment
demonstrated against a case nobody wrote a test for.

All nine `SUCCESS_CONDITION` items are satisfied; item 8 is satisfied by this verdict.

## NON-BLOCKING findings

Four, retained in full in the RAW record and not restated here in place of it:

| id | summary | severity |
|---|---|---|
| F-01 | the sealed AUDITOR expectation was materialized inside the IMPLEMENTER's change root by the full-clone custody pattern | non-blocking, **material** |
| F-02 | the result narrates worker PID 22700 while the log it cites records 15524 | non-blocking |
| F-03 | the deposit includes an undeclared `.gitattributes` (whose content is corrective) | non-blocking, beneficial |
| F-04 | `run/**`, the live E2E substrate, carries no identity fixation | non-blocking, observational |

## F-01 deserves the Controller's attention even though it does not block

The custody clone inside `50_CUSTODY\` has HEAD `4ec5e26` (02:37), later than my expectation deposit
`ebacef9` (01:23). It therefore placed my sealed expectation — and the whole P0C-001 audit record — on
the implementer's disk. `OPERATING_PROFILE_LITE` §3 is explicit that CLAUDE_A never reads the
expectation, because an implementer who has seen the checklist builds toward it.

I did not treat this as blocking, and I want the reasoning visible rather than buried. The implementer
disclosed it unprompted and named the exact paths it declined to open. Materialization is measurable;
reading is not — I can prove the file was there and cannot prove what was done with it, in either
direction. And the build's close fit to my criteria is independently explained, because the expectation
and the build were both written from the same frozen phase definition and implementation command, which
already required the N-3 negative controls, the autocrlf negative control and the single-cycle
dispatcher.

What should change is the mechanism, not this verdict: a sparse or path-filtered checkout that never
materializes `05_EVIDENCE/**/AUDIT/**` in an IMPLEMENTER envelope would make the separation structural
instead of attested. Until then, every future audit in this programme inherits the same unverifiable
assurance.

## C4 Article 33

T-2, T-3, T-4 are NOT MET. T-5 is NOT MET — a real one-line restore route exists.

**T-1 is NOT MET on the reading I registered before disclosure**, and I am not resolving its ambiguity
in my own favour. The substantive build sent nothing: no network code exists and all git activity was
local except read-only fetches. The authorized BUILD_READY deposit to a public repository does reach
outbound transmission and a third-party write, and R-05's classification of remote handoff as mechanical
custody — distinct from substantive work — is what keeps T-1 unfired. **If the Controller scopes that
deposit as part of P0.5 work, T-1 is MET and Secondary Audit becomes required.** That determination is
the Controller's to record.

`SECONDARY_AUDIT_REQUIRED = NO`, subject to that scoping question. A dispute over any finding here
(T-2) or a challenge to any measurement in it (T-3) would establish a trigger, and any Secondary
Auditor must be a new Context that does not read this verdict, its grounds, or the RAW body before
fixing its own RAW result.

## Correlated-failure limitation

I share model lineage with the IMPLEMENTER, and lineage independence was never available in this
programme. `OI-4` is unmitigated because HQ-G defers the different-lineage Auditor question. A reasoning
defect common to both contexts would pass this audit unseen. F-01 compounds it: the control that should
have kept the expectation away from the builder was an attestation rather than a mechanism. These two
limitations should be weighed together against the strength of the re-measured evidence above, not
netted out against it.

## Authority

This verdict grants nothing. It is not a Human Gate, not an approval, not implementation authority for
any later phase, and not canon promotion. It reports that the P0.5 local feasibility build satisfies
its stated completion gate. Whether P0.5 is declared complete, and what P1 is authorized to do, remain
Controller and Human Owner decisions.
