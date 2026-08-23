---
document_id: RIAN_CLAUDE_CONTROLLER_IMPLEMENTATION_ROADMAP
document_type: CONTROL_ROADMAP
revision: 1
updated_at_jst: 2026-08-23T09:54:00+09:00
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

RIAN does not implement the Task deliverable and does not independently audit work it directed.

## 3. Runtime-control architecture

Primary runtime control plane:
- Local Controller
- durable state / WAL
- lock / lease
- worker registry
- heartbeat
- PID/process reconciliation
- atomic ready markers
- runtime JSON

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

### Change start trigger

Human Owner supplies one bounded `START_REQUEST` for a local/candidate/mock change.

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
- current Change and Gate state.

Unmanaged Claude processes are detected and reported fail-closed. They are not automatically killed merely because they are unmanaged.

P6 visualizes this contract; P1 creates it.

## 6. Implementation roadmap

| Phase | 工程 | 主タスク | 完了条件 / Gate | Current state |
|---|---|---|---|---|
| **P0-A** | Bridge RC4 closeout | RC4 Human authority確認、RC4 identity確認、fresh Independent Audit | RC4 Audit PASS / MUST 0 / UNKNOWN 0 | **COMPLETE** |
| **P0-B** | Architecture Study governance closeout | C2第14条10条件化、consumer列挙、M5ラベル、stale state是正、freeze、独立監査 | Research Governance Audit PASS | **COMPLETE** |
| **P0-C** | Human Architecture Gate | HQ-A〜I一括判断。R-HYBRID、Human Gate方式、retry、Evidence、Git役割を固定 | Human Decision artifact fixed on exact candidate SHA | **COMPLETE** |
| **P0.5** | 技術成立性試験 | N-3 write isolation、headless Claude、RIAN Adapter feasibility、timeout/late/idempotency、credentialless mock、WAKE-only dispatcher、byte integrity | Primary Full Audit PASS + required Secondary Audit PASS/closed + MUST 0 + P0.5 load-bearing UNKNOWN 0 | **PRIMARY PASS / SECONDARY REQUIRED BY T-1 / OPEN** |
| **P1** | Local Controller骨格 + Runtime supervision | durable state/WAL、state machine、COMMAND/RESULT/AUDIT envelope、sequence、dedup、lock/lease、decision replay、START_REQUEST、atomic RESULT_READY/AUDIT_READY、Worker Registry、Heartbeat、PID reconciliation、Runtime JSON、unmanaged Claude detection、path-filtered custody | Local mock E2E PASS; restart/recovery PASS; runtime JSON accurately matches OS/process state; no AUDIT materialization into IMPLEMENTER envelope | **NOT STARTED** |
| **P2** | RIAN Adapter logical layer | RianTransport contract、credentialless mock、canonical loader、decision loader、Gate engine、Human Action判定、RIAN_INBOX event contract、deterministic decision replay | Controller→Rian Adapter→DecisionResult deterministic reproduction PASS in credentialless mock; no fabricated real transport; Human-boundary classification PASS | **NOT STARTED** |
| **P3** | Claude Direct Bridge / Group orchestration | measured headless Claude invocation、Claude A Engineering Group orchestration（Maker/Checker/Internal QA）、fresh-context rules、Claude B independent audit invocation、result ingestion、timeout/UNKNOWN、automatic custody | **人間copy/paste・手動Claude起床なしで1 bounded cycle完走** | **NOT STARTED** |
| **P4** | E2E + Attack Test | duplicate、late、partial、API断、stale state、PID reuse、heartbeat loss、unmanaged Claude、forged READY marker、write侵入、audit混線、expectation leakage、Human Gate bypass | Normal E2E PASS + Negative/Adversarial PASS | **NOT STARTED** |
| **P5** | SHADOW運転 | 実環境観測、Production write/output絶縁、長時間連続運転、host restart、controller restart、worker crash/recovery、stale lease recovery | Shadow Operational PASS with no Production/external effect | **NOT STARTED** |
| **P6** | Control Tower | Runtime JSON可視化、PJ Cell状態、Worker数/PID、Gate、Heartbeat、Evidence、Alarm、Human Action、STOP理由表示 | DCS画面で複数Cell/workerを監視可能 | **NOT STARTED** |
| **P7** | Production採用 | RC固定 → required Audit → Human Gate → 最小deploy → commissioning → Evidence → SEAL | Operational Complete | **NOT STARTED** |

## 7. P0.5 current task queue

1. Preserve Primary Full Audit R1 and RAW findings unchanged.
2. Controller records C4 Article 33 `T-1=MET` because authorized Git custody reached external transmission / third-party write.
3. Run a fresh `order: secondary / scope: process` Auditor Context.
4. Secondary Auditor must not read Primary finding body, grounds, verdict, or reasoning before fixing its own RAW result.
5. If Primary and Secondary disagree, pass both unchanged to Human Owner; Controller does not arbitrate.
6. If the required Secondary Audit passes and no new MUST/load-bearing UNKNOWN appears, close P0.5.
7. Start P1 automatically under the standing P0-C→P2 execution authorization.

## 8. P1 MUST additions from P0.5 lessons

P1 scope explicitly includes the following preventive controls:

- path-filtered/sparse custody so `AUDIT/**` is never materialized into an IMPLEMENTER workspace;
- Local Controller rather than Git polling as the primary runtime-state owner;
- worker registry + heartbeat + PID reconciliation;
- unmanaged Claude process alarm/state;
- durable START_REQUEST and terminal READY-marker contract;
- exact-byte/line-ending integrity;
- no blind resend;
- restart-safe INTENT/state replay;
- machine-readable `runtime_status.json`.

## 9. Phase boundary rule

No automatic phase transition occurs from a narrative status alone.

Advance requires objective evidence for the current phase completion gate.

Unexpected FAIL, out-of-spec behavior, identity mismatch, unknown dependency, or unresolved load-bearing UNKNOWN => fail-closed STOP.

No Production/SHADOW operation, live external send outside the specifically authorized handoff mechanism, credential/secret action, financial/trading/payment/order action, or canonical modification is implied by this roadmap.
