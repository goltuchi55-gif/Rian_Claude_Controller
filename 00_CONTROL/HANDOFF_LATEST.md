---
document_id: RIAN_CLAUDE_CONTROLLER_HANDOFF_LATEST
document_type: THREAD_HANDOFF
revision: 1
updated_at_jst: 2026-08-23T10:30:00+09:00
controller: RIAN
status: CURRENT
canonical_change: false
---

# Rian-Claude Controller | Thread Handoff

## 1. MISSION

Continue the Rian-Claude autonomous development-control project from the exact current Gate.

Immediate mission:

1. Complete the required P0.5 Secondary Process Audit.
2. If P0.5 closes PASS with no blocking MUST / load-bearing UNKNOWN, advance automatically to P1 under the standing Human authorization through P2.
3. In P1, build the durable Local Controller and runtime-supervision layer so Human copy/paste and manual `FIN` relay disappear from normal operation.
4. Use the newly available interactive Remote PowerShell channel as an engineering/commissioning channel, not as a replacement for the Local Controller or canonical governance.

Do not restart completed P0-A / P0-B / P0-C work.

---

## 2. CURRENT AUTHORITATIVE CONTROL STATE

Control repository:

`goltuchi55-gif/Rian_Claude_Controller`

Current status:

`00_CONTROL/CURRENT_STATUS.md`

Current active phase:

`P0.5`

Current state:

`PRIMARY_FULL_AUDIT_PASS__SECONDARY_PROCESS_AUDIT_EXPECTATION_READY`

P0-C is closed for the Human Architecture Decision.

No additional planned Human Gate exists through P2, subject to ACTIVE C1-C4, evidence/audit gates, fail-closed behavior, and non-waivable Human boundaries.

---

## 3. P0.5 CURRENT RESULT

### Technical build

BUILD_READY custody commit:

`4ec5e267efa317c9772fca1f7e1b50cbc17a881d`

Measured / re-measured result:

- SELF_TEST = PASS
- NEGATIVE_TEST = PASS
- N3_WRITE_ISOLATION = PASS
- HEADLESS_CLAUDE_FEASIBILITY = AVAILABLE
- RIAN_API_FEASIBILITY = NOT_AVAILABLE, with explicit fail-closed branch
- IDEMPOTENCY_TIMEOUT_LATE_RESPONSE = PASS
- CREDENTIALLESS_MOCK_E2E = PASS
- WAKE_TRIGGER_REMOVAL = PASS
- CORE_AUTOCRLF_CONTROL = PASS

### Primary Full Audit

Audit result commit:

`e64dbbfe4aba08e7d4c47f8fd25359258392611f`

Verdict:

- PASS
- OPEN_MUST = 0
- LOAD_BEARING_UNKNOWN = 0
- BLOCKING_FINDINGS = 0

The Primary RAW and verdict are immutable history.

### Primary non-blocking findings to retain

- F-01 MATERIAL: full-clone custody materialized AUDIT material into the IMPLEMENTER-side change root.
- F-02: result narrative PID and cited log PID differed.
- F-03: a directory-scoped `.gitattributes` was deposited although not declared in the original BUILD_READY list; it was beneficial for exact-byte integrity.
- F-04: `run/**` live E2E substrate had no fixed identity.

Do not erase these findings.

P1 MUST prevent F-01 structurally with path-filtered/sparse custody so `AUDIT/**` is never materialized into an IMPLEMENTER workspace.

---

## 4. C4 T-1 CONTROLLER DETERMINATION

Controller determination:

`00_CONTROL/P0_5-001/P0_5_001_T1_CONTROLLER_DETERMINATION_R1_20260823.md`

SHA256:

`8439e245e223eb13f7d6691c67a870cada85113a792e5e0b8b70d7718585afec`

Controller conclusion:

- T-1 = MET
- SECONDARY_AUDIT_REQUIRED = YES

Reason:

Authorized Git custody/handoff reached external transmission / third-party write. Permission to perform that handoff does not suppress the C4 Article 33 trigger.

Therefore P0.5 is still OPEN despite the Primary PASS.

---

## 5. IMMEDIATE NEXT COMMAND

Fresh Secondary AUDITOR Context only.

Command:

`00_CONTROL/P0_5-001/P0_5_001_SECONDARY_AUDIT_EXPECTATION_COMMAND_R1_20260823.md`

Expected SHA256:

`e4c87889017504e5dad439787daed75d25d8c5d81f3289cdacaba41ba95796aa`

Role:

- c4_role = AUDITOR
- order = secondary
- scope = process
- stage = expectation

C4 D-3 applies.

Before the Secondary Auditor fixes its own RAW result, it MUST NOT read:

- Primary finding body
- Primary grounds
- Primary verdict
- Primary reasoning

It may receive only the minimum target-identification information allowed by C4.

If Primary and Secondary disagree, both results are passed unchanged to Human Owner. RIAN/Controller does not arbitrate, merge, average, or majority-vote the verdicts.

---

## 6. P0.5 NEXT SEQUENCE

1. Fresh Secondary AUDITOR authors/seals its expectation.
2. Controller independently verifies expectation custody / exact bytes.
3. Controller releases only the Secondary process target.
4. Secondary AUDITOR fixes its own RAW result and verdict.
5. Controller checks actual Evidence, commit identity, SHA sidecars, MUST/UNKNOWN, and trigger conditions.
6. If Primary and Secondary disagree -> STOP and send both unchanged to Human Owner.
7. If Secondary closes PASS with no new blocking MUST / P0.5-load-bearing UNKNOWN -> close P0.5.
8. Automatically begin P1 under the standing through-P2 execution authorization.

Do not create a discretionary Human Gate between P0.5 and P1.

---

## 7. REVISED ROADMAP

Authoritative control roadmap:

`00_CONTROL/ROADMAP.md`

Revision:

`2`

SHA256:

`2ffb65a604347139db9019bd7afa881e2d5594cbd21c7da1c8d1c545a2458af3`

Current phase states:

- P0-A COMPLETE
- P0-B COMPLETE
- P0-C COMPLETE
- P0.5 PRIMARY PASS / SECONDARY REQUIRED BY T-1 / OPEN
- P1 NOT STARTED
- P2 NOT STARTED
- P3 NOT STARTED
- P4 NOT STARTED
- P5 NOT STARTED
- P6 NOT STARTED
- P7 NOT STARTED

---

## 8. ROLE TOPOLOGY

### RIAN

Canonical role class:

`CONTROLLER`

RIAN functions:

- authority/canonical loading
- COMMAND generation/freeze
- role assignment
- custody acceptance
- state/Gate decision
- Human escalation when required
- interactive remote read-only investigation / attended commissioning through the authorized remote terminal channel

RIAN MUST NOT:

- implement the Task deliverable
- author Auditor expectation text
- independently audit work it directed
- weaken audit verdicts
- treat Remote PowerShell access as authority expansion

### Claude A Group

Canonical role class:

`IMPLEMENTER`

Logical Engineering Group.

Internal functions may include:

- Maker / 作成
- Checker / 照査
- Internal QA
- self-test
- negative/adversarial test

These are internal Engineering functions, not new canonical role classes and not independent audit.

### Claude B Group

Canonical role class:

`AUDITOR`

Functions:

- expectation generation before disclosure
- read-only artifact/process audit
- PASS / FAIL / NEEDS_HUMAN judgment
- primary / secondary audit when triggered

---

## 9. NEW REMOTE POWERSHELL CAPABILITY

Remote Desktop Commander connection to the authorized development host has been successfully established.

RIAN has already performed a real read-only PowerShell/process probe through the remote channel.

Observed at the probe time:

- six `claude.exe` processes were present
- process PIDs observed: `14932`, `16760`, `24772`, `25212`, `44412`, `44656`

This was only a process-count snapshot. The six processes have NOT yet been classified into active / idle / stale / managed / unmanaged.

Do not kill or modify an unknown Claude process merely because it appears old or unmanaged.

### Remote channel role

The remote PowerShell channel MAY be used during an active RIAN interaction for:

- read-only filesystem/process investigation
- SHA/log/runtime-status verification
- process inventory
- attended startup of an already-authorized Local Controller or fresh Claude worker
- commissioning / recovery diagnostics

It is NOT:

- the autonomous Local Controller
- proof of an autonomous RIAN API
- a Human Gate bypass
- permission to cross Production / external-send / third-party-write / credential / secret / financial boundaries
- permission for RIAN to implement or independently audit

Remote terminal availability is capability, not authority.

---

## 10. P1 SCOPE | LOCAL CONTROLLER + RUNTIME SUPERVISION

P1 is the next major implementation phase after P0.5 closes.

P1 MUST include:

- durable state / WAL
- deterministic state machine
- COMMAND / RESULT / AUDIT envelopes
- sequence
- dedup
- lock / lease
- restart-safe INTENT and decision replay
- durable `START_REQUEST`
- atomic `RESULT_READY.json`
- atomic `AUDIT_READY.json`
- Worker Registry
- worker Heartbeat
- PID / OS-process reconciliation
- `runtime_status.json`
- expected / running / stale worker counts
- role / group / function / stage for each worker
- command SHA per worker
- lease/lock state
- unmanaged Claude process detection
- Local Controller health
- optional Remote Ops health `ONLINE / OFFLINE / UNKNOWN`
- path-filtered / sparse custody
- exact-byte / line-ending integrity
- no blind resend
- Remote Ops disconnect/reconnect must not mutate phase state by itself

P1 completion gate:

- Local mock E2E PASS
- restart/recovery PASS
- runtime JSON accurately matches OS/process state
- no AUDIT materialization into IMPLEMENTER envelope
- Remote Ops disconnect does not corrupt or advance runtime state

P1 creates the machine-readable runtime contract.

P6 only visualizes it.

---

## 11. START / COMPLETION OPERATING MODEL

### Controller startup

Target final design:

Local Controller starts automatically with the host using a bounded local startup mechanism such as Task Scheduler or a service, after the applicable phase Gate.

Automatic persistence of the external Remote MCP channel is NOT authorized merely by the roadmap.

### Change start

Human Owner supplies one bounded `START_REQUEST`.

For attended development, Human may issue START intent in chat and RIAN may materialize the bounded local `START_REQUEST` through Remote PowerShell when phase authority permits.

This is not a Production GO.

### Completion detection

Do not use narrative text such as `FIN` as the machine completion signal.

Each stage ends with an atomic machine-readable marker only after:

1. deliverable/evidence creation
2. manifest generation
3. detached SHA verification
4. self-test or audit completion
5. terminal-state fixation

Examples:

- `RESULT_READY.json`
- `AUDIT_READY.json`

Local Controller validates the marker and changes state.

RIAN may inspect the same state during attended operation, but RIAN inspection is not the primary completion trigger.

---

## 12. P2 SCOPE | RIAN ADAPTER LOGICAL LAYER

P2 MUST NOT assume an existing autonomous RIAN API.

Measured current state:

Real RIAN transport = `NOT_AVAILABLE`.

P2 therefore focuses on:

- `RianTransport` contract
- credentialless mock transport
- canonical loader
- decision loader
- Gate engine
- Human Action classification
- `RIAN_INBOX` event contract
- deterministic decision replay

Interactive:

`RIAN -> Remote Desktop Commander -> PowerShell`

is an attended engineering/operator path only.

It is NOT the autonomous P2 RianTransport.

P2 completion:

Controller -> Rian Adapter -> DecisionResult deterministic reproduction PASS in credentialless mock, with no fabricated real transport and correct Human-boundary classification.

---

## 13. P3 SCOPE | CLAUDE DIRECT BRIDGE / GROUP ORCHESTRATION

P3 is where the autonomous Claude execution loop is closed.

Scope:

- measured headless Claude invocation
- Claude A Engineering Group orchestration
  - Maker
  - Checker
  - Internal QA
- fresh Context rules
- Claude B independent audit invocation
- result ingestion
- timeout / UNKNOWN handling
- automatic custody

RIAN Remote PowerShell may be used for attended commissioning.

P3 completion requires:

`one bounded cycle with no Human copy/paste, no manual Claude wake, and no requirement for RIAN to remain continuously present in chat`

---

## 14. P4-P7

### P4 | E2E + Attack Test

Include at minimum:

- duplicate
- late
- partial result
- API disconnect
- stale state
- PID reuse
- heartbeat loss
- unmanaged Claude
- forged READY marker
- write-envelope intrusion
- audit mixing
- expectation leakage
- Human Gate bypass
- Remote Ops disconnect during attended commissioning

Completion:

Normal E2E PASS + Negative/Adversarial PASS.

### P5 | SHADOW

Production write/output isolated.

Test:

- long-duration operation
- host restart
- controller restart
- worker crash/recovery
- stale lease recovery

Remote RIAN channel is optional observation/recovery only, never a runtime dependency.

### P6 | Control Tower

Visualize the P1 runtime contract:

- PJ Cell state
- worker count / PID
- role / group / function
- Gate
- Heartbeat
- Evidence
- Alarm
- Human Action
- STOP reason
- Local Controller health
- Remote Ops health

Goal: DCS-like multi-cell supervision.

### P7 | Production

Sequence remains:

RC fix -> required Audit -> Human Gate -> minimal deploy -> commissioning -> Evidence -> SEAL

No Production write/config/runtime/credential/live financial action without the applicable action-specific Human Gate.

---

## 15. BINDING GOVERNANCE / DO NOT FORGET

ACTIVE C1-C4 remain highest authority.

Important operating rules:

- read-only investigation first
- minimal change only
- no opportunistic refactor
- implementation and independent audit separated
- Implementer self-test/internal QA != independent audit
- Auditor does not fix
- Controller does not implement deliverable
- Human Gate only after required audit/evidence PASS
- unexpected FAIL / out-of-spec / unknown dependency => fail-closed STOP
- no exception/test-skip/threshold relaxation to hide a defect
- audit correction loop is bounded
- Production / outbound / third-party write / credential / secret / money / trading boundaries remain Human-owned
- Git is not Production deploy
- do not treat technical connector permission as governance authority
- do not expose secrets or credential values in Git/Evidence

C4 is ACTIVE by the Human Activation decision even though the sealed C4 file's own historical frontmatter says activation not started.

Do not regress to the stale-frontmatter interpretation.

---

## 16. NEXT-THREAD OPENING ACTION

The next RIAN instance should:

1. Read:
   - `00_CONTROL/HANDOFF_LATEST.md`
   - `00_CONTROL/CURRENT_STATUS.md`
   - `00_CONTROL/ROADMAP.md`
2. Re-verify the latest Git state before relying on narrative history.
3. Re-check ACTIVE C1-C4 / Gate / role separation for the immediate Secondary Audit step.
4. Prefer direct Remote PowerShell execution over asking Human to relay PowerShell commands, when the action is within current authority.
5. Begin by checking whether the Secondary Audit expectation/result has already appeared.
6. If not, use the fresh Secondary AUDITOR command already issued.
7. Do not advance to P1 until the Secondary Audit completion condition is actually met.

---

## 17. HUMAN OWNER EXPECTED EXPERIENCE

Near-term attended mode:

`Human gives START / intent -> RIAN uses Remote PowerShell directly -> Claude/Git/Evidence progress -> Human is not a command courier`

Target autonomous mode after P1-P3:

`Human START once -> Local Controller runs Claude A/B workflow -> machine READY markers drive transitions -> RIAN/Human are called only for unresolved decisions, abnormal states, or non-waivable Gates`

This is the target operating model.
