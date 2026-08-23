---
document_id: RIAN_CLAUDE_CONTROLLER_IMPLEMENTATION_ROADMAP
document_type: CONTROL_ROADMAP
revision: 2
updated_at_jst: 2026-08-23T10:23:00+09:00
controller: RIAN
status: ACTIVE_CONTROL_ROADMAP
canonical_change: false
---

# Rian-Claude Controller Implementation Roadmap

## 1. Mission

Build a fail-closed autonomous development control system in which:

- RIAN is the supervisory/controller decision layer, not the always-running runtime process;
- the Local Controller is the durable runtime control plane/state machine;
- Claude A is an Engineering Group inside the canonical `IMPLEMENTER` role class;
- Claude B is the Independent Audit Group inside the canonical `AUDITOR` role class;
- Git is a versioned handoff/evidence/anchor layer, not a Production deploy mechanism and not the primary runtime signal bus;
- Remote Desktop Commander / PowerShell is an optional **interactive RIAN remote-operations channel** for read-only investigation, attended commissioning, recovery, and authorized worker/process launch;
- the interactive remote-operations channel is **not** the autonomous Local Controller, not an autonomous RIAN API transport, not a Human Gate bypass, and not an authority expansion;
- Human Owner starts a bounded change and intervenes only at non-waivable Human boundaries or unresolved Human-owned decisions.

The Human authorization for autonomous execution through P2 remains subject to ACTIVE C1-C4, evidence gates, independent-audit gates, fail-closed behavior, and non-waivable Production / external-send / third-party-write / credential / secret / financial boundaries.

## 2. Role topology

### Claude A Group — Engineering Group

Canonical role class: `IMPLEMENTER`.

Internal functions may include:
- Maker / 作成
- Checker / 照査
- Internal QA / self-test / negative test

These functions are not new canonical role classes and do not constitute independent audit.

### Claude B Group — Independent Audit Group

Canonical role class: `AUDITOR`.

Functions:
- expectation generation/seal-before-disclosure
- read-only artifact/process audit
- PASS / FAIL / NEEDS_HUMAN judgment
- primary / secondary audit as triggered by C4

### RIAN

Canonical role class: `CONTROLLER`.

Functions:
- authority/canonical loading
- COMMAND generation/freeze
- role assignment
- custody acceptance
- state/gate decision
- Human escalation when required
- interactive remote read-only investigation / attended commissioning through an authorized remote terminal channel

RIAN does not implement the Task deliverable and does not independently audit work it directed.
Remote PowerShell access does not change those role limits.

## 3. Runtime-control architecture

### Primary runtime control plane

- Local Controller
- durable state / WAL
- lock / lease
- worker registry
- heartbeat
- PID/process reconciliation
- atomic ready markers
- runtime JSON

### Interactive RIAN remote-operations channel

Measured capability exists for an authorized Remote Desktop Commander connection to the development host and PowerShell execution during an active RIAN interaction.

Permitted purpose is supervisory/engineering work within the current phase authority, such as:
- read-only filesystem/process inspection;
- SHA/log/runtime-status verification;
- attended startup of an already-authorized local Controller or fresh Claude worker;
- commissioning and recovery diagnostics.

It is **not**:
- the always-running Local Controller;
- proof of an autonomous RIAN API;
- permission to cross Production / external-send / third-party-write / credential / secret / financial boundaries;
- permission for RIAN to author implementation deliverables or independent-audit results.

Loss of the remote channel must not corrupt the Local Controller state machine. Autonomous runtime operation must remain fail-closed and recoverable without assuming RIAN is continuously online.

### Git role

Git is used for:
- COMMAND
- RESULT
- AUDIT
- Evidence
- SHA sidecars
- versioned external anchor / historian

Git is not the primary real-time runtime state bus.

## 4. Start / completion operating model

### Controller startup

The Local Controller is intended to start automatically with the host by a bounded local startup mechanism such as Windows Task Scheduler or a service, subject to the phase-specific gate.

The interactive Remote MCP process may be used as an attended engineering/maintenance channel. Automatic startup or persistence of that external remote channel is **not authorized merely by this roadmap** and requires the applicable phase boundary/Gate check before configuration.

### Change start trigger

Human Owner supplies one bounded `START_REQUEST` for a local/candidate/mock change.

During attended development, the Human Owner may issue the START intent in chat and RIAN may materialize the bounded local `START_REQUEST` through the authorized remote PowerShell channel when the current phase authority permits it.

This is not a Production GO and does not authorize any non-waivable effect.

### Completion detection

Claude workers do not signal completion by chat text such as `FIN`.

The final step of each stage creates an atomic machine-readable terminal marker such as:

- `RESULT_READY.json`
- `AUDIT_READY.json`

The marker is written only after:
1. deliverable/evidence creation;
2. manifest generation;
3. detached SHA verification;
4. self-test or audit completion;
5. terminal state fixation.

Local Controller validates the marker and transitions the state machine.

RIAN may inspect the same state and evidence through PowerShell during attended operation, but RIAN inspection is not the primary completion trigger.

## 5. Runtime observability contract

P1 SHALL include a machine-readable runtime view sufficient to answer:

- how many managed Claude processes exist;
- expected vs running vs stale workers;
- role/group/function/stage of each worker;
- worker PID;
- command SHA;
- heartbeat sequence/time;
- current state;
- lease/lock state;
- unmanaged Claude process detection;
- current Change and Gate state;
- Local Controller health;
- optional interactive RIAN remote-operations channel health (`ONLINE / OFFLINE / UNKNOWN`) without making that channel a runtime dependency.

Unmanaged Claude processes are detected and reported fail-closed. They are not automatically killed merely because they are unmanaged.

P6 visualizes this contract; P1 creates it.

## 6. Implementation roadmap

| Phase | 工程 | 主タスク | 完了条件 / Gate | Current state |
|---|---|---|---|---|
| **P0-A** | Bridge RC4 closeout | RC4 Human authority確認、RC4 identity確認、fresh Independent Audit | RC4 Audit PASS / MUST 0 / UNKNOWN 0 | **COMPLETE** |
| **P0-B** | Architecture Study governance closeout | C2第14条10条件化、consumer列挙、M5ラベル、stale state是正、freeze、独立監査 | Research Governance Audit PASS | **COMPLETE** |
| **P0-C** | Human Architecture Gate | HQ-A〜I一括判断。R-HYBRID、Human Gate方式、retry、Evidence、Git役割を固定 | Human Decision artifact fixed on exact candidate SHA | **COMPLETE** |
| **P0.5** | 技術成立性試験 | N-3 write isolation、headless Claude、RIAN Adapter feasibility、timeout/late/idempotency、credentialless mock、WAKE-only dispatcher、byte integrity | Primary Full Audit PASS + required Secondary Audit PASS/closed + MUST 0 + P0.5 load-bearing UNKNOWN 0 | **PRIMARY PASS / SECONDARY REQUIRED BY T-1 / OPEN** |
| **P1** | Local Controller骨格 + Runtime supervision | durable state/WAL、state machine、COMMAND/RESULT/AUDIT envelope、sequence、dedup、lock/lease、decision replay、START_REQUEST、atomic RESULT_READY/AUDIT_READY、Worker Registry、Heartbeat、PID reconciliation、Runtime JSON、unmanaged Claude detection、Local Controller health、Remote Ops health observation、path-filtered custody | Local mock E2E PASS; restart/recovery PASS; runtime JSON accurately matches OS/process state; no AUDIT materialization into IMPLEMENTER envelope; Remote Ops disconnect does not corrupt or advance runtime state | **NOT STARTED** |
| **P2** | RIAN Adapter logical layer | RianTransport contract、credentialless mock、canonical loader、decision loader、Gate engine、Human Action判定、RIAN_INBOX event contract、deterministic decision replay。Interactive RIAN→Remote PowerShell path is treated only as an attended operator/commissioning path, not autonomous RianTransport | Controller→Rian Adapter→DecisionResult deterministic reproduction PASS in credentialless mock; no fabricated real autonomous transport; Human-boundary classification PASS | **NOT STARTED** |
| **P3** | Claude Direct Bridge / Group orchestration | measured headless Claude invocation、Claude A Engineering Group orchestration（Maker/Checker/Internal QA）、fresh-context rules、Claude B independent audit invocation、result ingestion、timeout/UNKNOWN、automatic custody。RIAN Remote PowerShell may be used for attended commissioning, while final cycle execution must be Local-Controller-driven | **人間copy/paste・手動Claude起床なし、かつRIANの連続対話参加なしで1 bounded cycle完走** | **NOT STARTED** |
| **P4** | E2E + Attack Test | duplicate、late、partial、API断、stale state、PID reuse、heartbeat loss、unmanaged Claude、forged READY marker、write侵入、audit混線、expectation leakage、Human Gate bypass、Remote Ops disconnect during attended commissioning | Normal E2E PASS + Negative/Adversarial PASS | **NOT STARTED** |
| **P5** | SHADOW運転 | 実環境観測、Production write/output絶縁、長時間連続運転、host restart、controller restart、worker crash/recovery、stale lease recovery。RIAN remote channel is optional for observation/recovery and must not be a runtime dependency | Shadow Operational PASS with no Production/external effect from the controlled SHADOW workload; Local Controller continues fail-closed if RIAN remote channel is absent | **NOT STARTED** |
| **P6** | Control Tower | Runtime JSON可視化、PJ Cell状態、Worker数/PID、Gate、Heartbeat、Evidence、Alarm、Human Action、STOP理由、Local Controller health、Remote Ops connection health表示 | DCS画面で複数Cell/workerを監視可能 | **NOT STARTED** |
| **P7** | Production採用 | RC固定 → required Audit → Human Gate → 最小deploy → commissioning → Evidence → SEAL | Operational Complete | **NOT STARTED** |

## 7. P0.5 current task queue

1. Preserve Primary Full Audit R1 and RAW findings unchanged.
2. Controller records C4 Article 33 `T-1=MET` because authorized Git custody reached external transmission / third-party write.
3. Run a fresh `order: secondary / scope: process` Auditor Context.
4. Secondary Auditor must not read Primary finding body, grounds, verdict, or reasoning before fixing its own RAW result.
5. If Primary and Secondary disagree, pass both unchanged to Human Owner; Controller does not arbitrate.
6. If the required Secondary Audit passes and no new MUST/load-bearing UNKNOWN appears, close P0.5.
7. Start P1 automatically under the standing P0-C→P2 execution authorization.

The newly measured Remote PowerShell capability does not waive this queue and does not reopen the Primary Audit.

## 8. P1 MUST additions from P0.5 and Remote Ops lessons

P1 scope explicitly includes the following preventive controls:

- path-filtered/sparse custody so `AUDIT/**` is never materialized into an IMPLEMENTER workspace;
- Local Controller rather than Git polling or RIAN chat presence as the primary runtime-state owner;
- worker registry + heartbeat + PID reconciliation;
- unmanaged Claude process alarm/state;
- durable START_REQUEST and terminal READY-marker contract;
- exact-byte/line-ending integrity;
- no blind resend;
- restart-safe INTENT/state replay;
- machine-readable `runtime_status.json`;
- Local Controller health in runtime status;
- optional Remote Ops health observation, without making Remote MCP a runtime dependency;
- attended RIAN PowerShell actions must preserve role separation and current write envelopes;
- disconnect/reconnect of the Remote Ops channel must not mutate phase state by itself.

## 9. Operating modes

### Development / attended mode

Human starts the change. RIAN may directly use the authorized remote PowerShell channel for read-only investigation, SHA/log verification, process inventory, and phase-authorized startup/commissioning actions.

This removes Human copy/paste as an operator relay during attended development.

### Autonomous mode

Local Controller owns the runtime state machine and starts/monitors Claude workers from machine-readable state. RIAN is not required to remain continuously online.

### Recovery / commissioning mode

RIAN may reconnect through the authorized remote terminal channel to investigate stale workers, heartbeat loss, process/runtime JSON mismatch, or recovery conditions. Investigation begins read-only and remains within the current Gate/role/write authority.

## 10. Phase boundary rule

No automatic phase transition occurs from a narrative status alone.

Advance requires objective evidence for the current phase completion gate.

Unexpected FAIL, out-of-spec behavior, identity mismatch, unknown dependency, or unresolved load-bearing UNKNOWN => fail-closed STOP.

Remote terminal availability is an operational capability, not authority. It must never be interpreted as permission to bypass role separation, independent audit, Human Gate, or non-waivable boundaries.

No Production/SHADOW operation, live external send outside the specifically authorized handoff mechanism, credential/secret action, financial/trading/payment/order action, or canonical modification is implied by this roadmap.
