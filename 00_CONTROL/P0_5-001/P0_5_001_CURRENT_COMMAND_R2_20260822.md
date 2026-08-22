---
document_id: P0_5_001_CURRENT_COMMAND_R2
document_type: CONTROLLER_COMMAND
revision: 2
change_id: P0_5-001
phase: P0.5
issued_by: RIAN_CONTROLLER
role: CLAUDE_A
c4_role: IMPLEMENTER
stage: PHASE_BASIS_DISCOVERY
scope: P0_5_BRIDGE_BOOTSTRAP_BASIS_ONLY
issued_at_jst: 2026-08-22T23:59:00+09:00
status: ACTIVE
---

# P0.5-001 Current Command R2

## Mission

Start P0.5 with read-only / planning-first discipline. Authenticate the phase basis, confirm the applicable C1-C4 / Operating Profile constraints, and define the narrowest technically valid next step before any P0.5 implementation.

The P0-C Human Architecture decision is now issued and P0-C is closed for architecture decision purposes.

## Authority inputs

Authenticate before relying on them:

1. `00_HUMAN/P0C-001/P0C_001_HUMAN_ARCHITECTURE_DECISION_APPROVE_20260822.md`
2. `00_CONTROL/P0C-001/P0_TO_P2_AUTONOMOUS_EXECUTION_DECISION_20260822.md`
3. `05_EVIDENCE/P0C-001/PRIMARY_AUDIT/RESULT/SUPPLEMENT_R2/P0C_001_PRIMARY_AUDIT_VERDICT_R2_20260822.md`
4. the Human-issued R8 canonical-copy authority authenticated by that audit
5. ACTIVE C1-C4 / OPERATING_PROFILE through the R8-authorized Git read/use copy while measured identities match
6. the user-approved roadmap definition for P0.5: N-3 write isolation, headless Claude feasibility, Rian API feasibility, timeout/late-response/idempotency, credentialless mock testing

## Work

This R2 stage is read-only except for creation of P0.5 planning/evidence artefacts and permitted Git handoff.

1. Locate and inventory every authoritative or previously approved source that defines P0.5 / P1 / P2 scope, order, completion conditions, role separation, and implementation constraints.
2. Build a P0.5 phase-basis table using `MUST / MAY / SUGGEST / UNKNOWN` and preserve Human-owned decisions exactly.
3. Confirm whether the P0-C Human Architecture APPROVE resolves every HQ dependency relevant to P0.5 planning and local/mock implementation.
4. Record the observed bridge defects from P0-C as measured evidence:
   - RIAN can write Git COMMANDs;
   - Claude can push RESULTs after clean handoff bootstrap;
   - RIAN can read Git RESULTs;
   - Human observation/manual trigger was still needed to wake the next Claude step;
   - ambiguous/dirty worktree state broke handoff until a clean dedicated clone was introduced.
5. Define the minimum local dispatcher / worker / handoff boundary needed to eliminate the Human trigger without crossing Production, credential, money, external-send, or canonical-write boundaries.
6. Resolve the review tier for the first P0.5 implementation change. If it is a platform/shared-dependency/security/guard change, use FULL AUDIT.
7. Confirm whether a separate pre-implementation Plan audit is required. Do not invent one if OPERATING_PROFILE does not require it.
8. Define the first implementation package as a minimal, reversible candidate change only. No actual implementation in this R2 stage.
9. Do not modify canonical text, P0-C history, α/β/γ, Production, runtime, credentials, external systems, or money/trading behavior.
10. Do not make a real Claude/OpenAI/Anthropic model call in this stage.

## Required result

Create and push to:

`05_EVIDENCE/P0_5-001/BASIS_DISCOVERY/RESULT/`

- `P0_5_001_PHASE_BASIS_R2_20260822.md`
- detached `.sha256`

The result must contain:

- AUTHORITY_SOURCES
- PHASE_DEFINITION
- MUST
- MAY
- SUGGEST
- UNKNOWN
- HQ_DECISION_DEPENDENCY
- BRIDGE_DEFECT_MEASUREMENTS
- FIRST_IMPLEMENTATION_BOUNDARY
- REVIEW_TIER
- PLAN_AUDIT_REQUIRED
- COMPLETION_GATE_FOR_P0_5
- NEXT_SAFE_ACTION
- OPEN_MUST
- LOAD_BEARING_UNKNOWN
- HUMAN_DECISION_REQUIRED_NOW

If authoritative scope is insufficient, return `PHASE_DEFINITION=UNKNOWN` and the minimum unresolved item. Do not fill gaps by inference.

## Return

STATUS=
PHASE_DEFINITION=
HQ_DECISION_DEPENDENCY=
REVIEW_TIER=
PLAN_AUDIT_REQUIRED=
OPEN_MUST=
LOAD_BEARING_UNKNOWN=
HUMAN_DECISION_REQUIRED_NOW=
RESULT_PATH=
RESULT_SHA256=
GIT_COMMIT_SHA=

Then wait for Controller review.
