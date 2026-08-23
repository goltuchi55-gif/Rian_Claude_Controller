---
document_id: P0_5_001_PRIMARY_AUDIT_RAW_FINDINGS_R1
document_type: PRIMARY_AUDIT_RAW_FINDINGS
change_id: P0_5-001
phase: P0.5
auditor: CLAUDE_B / C4_ROLE=AUDITOR / ORDER=PRIMARY
issued_under: P0_5_001_FULL_AUDIT_RELEASE_COMMAND_R1 (4f06646f…306e)
issued_at_jst: 2026-08-23
status: RAW_IMMUTABLE
judged_against: P0_5_001_AUDIT_EXPECTATION_R1_20260823.md (a5a46fda…928b)
---

# P0.5-001 Primary Audit — RAW Findings

RAW. Not replaced by the verdict, not repaired, not rewritten. Read-only audit: no correction was
performed and no build artefact was altered.

## 0. Identity and manifest integrity

| item | expected | measured | result |
|---|---|---|---|
| sealed expectation (local + origin) | `a5a46fda…928b` | identical both | unaltered |
| implementation result | `65689951…e8a5` | identical | MATCH (command + sidecar) |
| build manifest | `b5aa81d2…73c7` | identical | MATCH (command + sidecar) |
| identity summary | `c738e4fd…e09f` | identical | MATCH (command + sidecar) |
| local manifest vs actual files — **audit start** | 29 rows | 29 match | 0 mismatch, 0 missing |
| local manifest vs actual files — **audit end** | 29 rows | 29 match | **0 changed** |

Start and end recomputation agree, so this result is adoptable under release-command item 4.

## 1. Verified by re-measurement, not accepted on narrative

| # | claim | method | result |
|---|---|---|---|
| V-1 | SELF_TEST 84 tests PASS | re-ran the full unit suite myself | **84 run, 0 failures, 0 errors — reproduced** |
| V-2 | N-3 allowlist is absolute and fail-closed | copied the whole build to a scratch path and ran it | **denied `OUTSIDE_ALLOWLIST`** — containment held against relocation. Strongest single piece of evidence in this build; the control refused a path it had never seen. |
| V-3 | no live model request possible | read `headless_probe.py` | `_ALLOWED_ARGV_TAILS` is a closed 2-tuple (`--version`, `--help`), `ProbeRefused` on anything else, child stdin `DEVNULL`. Structural, not asserted. |
| V-4 | no network capability | grepped all of `src`, `tests`, `tools` for socket/http/urllib/requests/ssl/smtp | **none found** |
| V-5 | SHA authenticated before dispatch | read `dispatcher.py` control flow | `integrity.read_exact` at line 124 precedes `subprocess.Popen` at line 172; integrity failure records `DENIED_INTEGRITY` and never launches |
| V-6 | blind resend impossible | read `intent_store.assert_dispatch_allowed` | refuses when already terminal, and when attempts>0 while outcome retrieval unmeasured |
| V-7 | credential refusal | read `worker.py` | exits 78 on any credential-shaped env var; dispatcher builds child env from an allowlist |
| V-8 | one bounded WAKE cycle | read `logs/wake_cycle.json` | `human_wake_events=0`, `cycles=1`, `terminal_writes=1`, `exited_after_one_cycle=true`, second wake `NO_NEW_COMMAND` |
| V-9 | byte-integrity negative control genuinely fails | read `logs/byte_integrity.json` | positive 29→29 bytes preserved; negative 29→34 bytes, `conversion_detected=true`; global `core.autocrlf` `<unset>` before and after |
| V-10 | RIAN claim discipline | read full `rian_api_feasibility.json` | `NOT_AVAILABLE` measured; `network_call_made=false`; the adjacent `openai.EXE` is recorded with `is_rian_transport:false` and never invoked; explicit fail-closed downstream branch present |
| V-11 | no source published | listed every path on `origin/main` | no `.py`, no `src/p05`, no `10_IMPLEMENTER`; deposits confined to `00_CONTROL/P0_5-001/` and `05_EVIDENCE/P0_5-001/` |

**Correction to my own working note:** an initial query of mine appeared to show `adjacent_observations`
empty and `real_transport_implemented` absent. That was my wrong key path — both exist nested under
`evidence`. The narrative is accurate; no finding arises. Recorded because the RAW record should show
what I checked and got wrong, not only what survived.

## 2. Findings

### F-01 — the sealed AUDITOR expectation was materialized inside the IMPLEMENTER's change root — NON-BLOCKING, MATERIAL

**Where:** `C:\Projects\RIAN_CLAUDE_BRIDGE_P0_5_001_20260823\50_CUSTODY\_HANDOFF_R1\Rian_Claude_Controller\`
— a full clone of the handoff repository, checked out inside the IMPLEMENTER's own change root.

**Defect:** that clone's HEAD is `4ec5e26` (2026-08-23 02:37), which is *later* than my expectation
deposit `ebacef9` (01:23). It therefore contains, on the implementer's disk:
`05_EVIDENCE/P0_5-001/AUDIT/EXPECTATION/CUSTODY_PENDING/P0_5_001_AUDIT_EXPECTATION_R1_20260823.md`,
and additionally the entire P0C-001 audit record — RAW findings and verdicts R1 and R2.
`OPERATING_PROFILE_LITE` §3 states CLAUDE_A never reads the expectation, "including after the audit —
an implementer who has seen the checklist starts building toward it." Here that separation rests on an
assertion rather than a mechanism: the approved full-clone custody pattern places the checklist in the
builder's hands.

**How found:** listed the change root, spotted the custody clone containing `05_EVIDENCE/P0_5-001/AUDIT/`,
then compared that clone's HEAD commit date against the expectation deposit commit date.

**Blocking:** no, for three reasons stated plainly. The implementer disclosed it proactively and
unprompted, naming the exact paths it declined to open. I can measure materialization but cannot
verify a negative — no evidence of reading exists either way. And the alignment between the build and
my expectation is independently explained: both derive from the same frozen phase definition and
implementation command R3, which already mandated the N-3 negative controls, the autocrlf negative
control and the one-cycle dispatcher.

**Recommendation (not a repair):** the custody pattern should use a sparse or path-filtered checkout so
`05_EVIDENCE/**/AUDIT/**` is never materialized in an IMPLEMENTER envelope. That converts the control
from attestation to mechanism.

### F-02 — a narrative figure does not match the evidence it cites — NON-BLOCKING

**Where:** `P0_5_001_IMPLEMENTATION_RESULT_R1_20260823.md`, CREDENTIALLESS_MOCK_E2E: "worker subprocess
PID 22700 exited 0", citing `logs/wake_cycle.json`.

**Defect:** that log records `worker_pid: 15524` in both `cycle` and `live.first_cycle`. The narrative
cites a PID from a different run than the sealed log it references.

**How found:** read the stated PID out of the result, then read the PID out of the cited log. My own
re-run did not regenerate the log — all 29 manifested files were unchanged afterwards — so the log is
the original.

**Blocking:** no. The PID is incidental and every load-bearing value in that section matches the log
exactly (`worker_returncode=0`, `terminal_state=COMPLETED`, `terminal_writes=1`). Reported because
HQ-E requires evidence produced at the point of measurement rather than reconstructed from narrative,
and this is a small, real instance of narrative drifting from its evidence.

### F-03 — the deposit contains one undeclared file — NON-BLOCKING, BENEFICIAL

**Where:** `05_EVIDENCE/P0_5-001/IMPLEMENTATION/BUILD_READY/.gitattributes`.

**Defect:** the implementation command's HANDOFF enumerates the result, manifest, their sidecars and an
identity summary. `.gitattributes` is outside that list.

**How found:** compared the deposited path list on `origin/main` against the command's enumeration.

**Blocking:** no, and its content is corrective rather than harmful: `* text eol=lf` pins the directory
against line-ending conversion, which is exactly the defect that breaks detached-sidecar verification
elsewhere in this repository (`.sha256` files are not covered by the repo-root `.gitattributes`, so
they check out CRLF-converted on Windows). Recorded for deposit-discipline accuracy, not to discourage
the fix.

### F-04 — the live E2E evidence substrate carries no identity fixation — NON-BLOCKING, OBSERVATIONAL

**Where:** `10_IMPLEMENTER/run/**`, deliberately excluded from the build manifest.

**Defect:** `run/live_cycle/**` holds the actual COMMAND, result and state files behind the
CREDENTIALLESS_MOCK_E2E and WAKE_TRIGGER_REMOVAL claims, but nothing hashes it. A later reader cannot
re-verify the exact inputs of the live cycle; re-running regenerates them.

**How found:** cross-read the manifest scope against the paths referenced by `logs/wake_cycle.json`.

**Blocking:** no. `logs/wake_cycle.json` *is* manifested and records the measured outcome including the
command's expected SHA256, so the claim itself is identity-fixed. The exclusion is also what makes the
suite safely re-runnable, which is how I reproduced the 84 tests without disturbing the target.

## 3. SUCCESS_CONDITION assessment

| # | condition | result |
|---|---|---|
| 1 | N-3 isolation and negative controls PASS | **SATISFIED** — 16 unit + 10 driver denials; containment additionally proven live against a relocated copy (V-2) |
| 2 | headless feasibility measured with no live model request | **SATISFIED** — `AVAILABLE`; prompt submission structurally impossible |
| 3 | RIAN classified by contract + credentialless mock, nothing invented | **SATISFIED** — `NOT_AVAILABLE` measured; `transport_for()` refuses to return a real transport |
| 4 | timeout/late/duplicate/idempotency, durable INTENT, no blind resend, real retry disabled | **SATISFIED** — 6/6 scenarios; `real_provider_retry_enabled` is a derived property with no setter |
| 5 | credentialless mock E2E PASS | **SATISFIED** |
| 6 | WAKE-only one bounded cycle, no Human wake | **SATISFIED** — `human_wake_events=0`, exits after one cycle |
| 7 | clean custody paths, `core.autocrlf=false`, line-ending negative control | **SATISFIED** — global config `<unset>` before and after |
| 8 | independent Full Audit PASS, OPEN_MUST=0, no load-bearing UNKNOWN | **SATISFIED by this audit** |
| 9 | no Production/Gate/credential/financial/canonical/unauthorized send | **SATISFIED** — none found; no network code exists |

## 4. OPEN_MUST and UNKNOWN

`OPEN_MUST = 0` — every required capability is implemented, exercised and evidenced; I re-measured
rather than accepted each load-bearing one.

`LOAD_BEARING_UNKNOWN = 0`. The five carried unknowns are genuinely not load-bearing for P0.5: real
RIAN transport (no transport used — the worker is a stub), provider idempotency/outcome retrieval
(measuring it needs an outbound call and credential, both OUT_OF_SCOPE; retry stays disabled),
signing-key storage (signed Gate OUT_OF_SCOPE, R-09), unattended spot-check design (single
auto-stopping cycle, R-10), and headless behaviour under real invocation (a P1 question). Each has an
explicit fail-closed branch and none silently narrows a MUST.

## 5. C4 Article 33

| trigger | status |
|---|---|
| **T-1** | **NOT MET**, caveat recorded as pre-registered in the sealed expectation. The substantive build performed no external send: no network code exists in the package and all git activity was local except read-only fetches. The authorized BUILD_READY deposit to a public repository does reach outbound transmission and a third-party write, but R-05 classifies remote handoff as a mechanical custody process distinct from the substantive work. **If the Controller scopes that deposit as P0.5 work, T-1 flips to MET and Secondary Audit becomes required.** I flagged this before disclosure and I have not resolved it in my own favour. |
| **T-2** | NOT MET — no finding has been disputed |
| **T-3** | NOT MET — no measurement in this audit has been challenged |
| **T-4** | NOT MET — not requested by the Human Owner |
| **T-5** | **NOT MET** — a genuine one-line restore route exists and is stated; `rollback.cmd` carries the cmd.exe equivalent, and the envelope was empty before the build, so clearing it restores the prior state exactly |

`SECONDARY_AUDIT_REQUIRED = NO`, subject to the T-1 scoping question above.

## 6. Correlated-failure limitation

I share model lineage with the IMPLEMENTER. Role hygiene held — I wrote no build artefact and the
implementer wrote none under `40_AUDIT\` (its own negative control proves that directory is denied to
it) — but lineage independence was never available. `OI-4` is unmitigated and HQ-G defers the
different-lineage Auditor question, so a defect in reasoning that both contexts share would survive
this audit unseen. F-01 compounds this: the mechanism that should have kept the expectation away from
the builder did not exist, and the assurance there is an attestation I cannot test. A reviewer weighing
this PASS should weigh those two together.
