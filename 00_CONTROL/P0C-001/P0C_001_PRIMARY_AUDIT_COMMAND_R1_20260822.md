---
document_id: P0C_001_PRIMARY_AUDIT_COMMAND
document_type: AUDIT_COMMAND
revision: 1
change_id: P0C-001
role: AUDITOR
order: PRIMARY
stage: EXPECTATION
issued_by: RIAN_CONTROLLER
human_authority: P0C-001_HANDOFF_GIT_WRITE_APPROVED_20260822
scope: EXPECTATION_ONLY_BEFORE_TARGET_DISCLOSURE
creates_no_production_authority: true
creates_no_canonical_write_authority: true
---

# P0-C-001 Primary Audit Command R1

## MISSION

Create and seal the PRIMARY AUDITOR expectation for P0-C-001 before reading any audit target.

## AUTHORITY

Use only authenticated ACTIVE canon / operating documents and the frozen P0-C-001 Master/COMMAND required to determine scope.

Known frozen P0-C-001 Master:
`C:\Projects\RIAN_CLAUDE_BRIDGE_P0C_001_20260821\50_RIAN_CONTROLL\P0C_001_HQ_A_TO_I_MASTER_DISPATCH_DIRECTIVE_20260821.md`

Expected SHA256:
`881d58f13ccdc20dbb02418627395a5e56ddab64e937537d8cafea7f3838fe3d`

Git canonical reference:
`goltuchi55-gif/quicktrend-governance-canon-ref`

## MUST

1. Verify the frozen Master SHA256 before reading it.
2. Do not open any audit target before the expectation is sealed.
3. Do not read:
   - `10_ALPHA\`
   - `20_BETA\`
   - `30_GAMMA\`
   - `P0C_001_RIAN_CONSOLIDATED_HUMAN_DECISION_CANDIDATE_R1_20260822.md`
4. Resolve C4 Article 33 T-1 and T-5 from the frozen Master/COMMAND and record whether SECONDARY audit is required.
5. Write the expectation yourself as AUDITOR. RIAN/Controller does not author the expectation body.
6. Keep the expectation short. OPERATING_PROFILE_LITE §3 guidance is normally 10–30 lines and must include:
   - what the COMMAND requires in your own words,
   - what you will check and how,
   - what would make the audit fail,
   - seal-order declaration stating what you had read and had not read at seal time.
7. Save locally:
   `C:\Projects\RIAN_CLAUDE_BRIDGE_P0C_001_20260821\40_INDEPENDENT_AUDIT\P0C_001_PRIMARY_AUDIT_EXPECTATION_R1_20260822.md`
8. Create detached SHA256 sidecar for that file.
9. Push only the sealed expectation and its SHA256 sidecar to:
   `goltuchi55-gif/Rian_Claude_Controller`
   under:
   `05_EVIDENCE/P0C-001/PRIMARY_AUDIT/`
10. No Production, runtime, credential, canonical-text, Alpha/Beta/Gamma, or RIAN-candidate modification is authorized.
11. No force-push, history rewrite, branch deletion, or unrelated repository change.
12. After the expectation and sidecar are pushed, STOP before reading any audit target.

## TERMINAL RETURN

Return only:

STATUS=
EXPECTATION_LOCAL_PATH=
EXPECTATION_SHA256=
HANDOFF_REPO=
HANDOFF_PATH=
GIT_COMMIT_SHA=
T1=
T5=
SECONDARY_AUDIT_REQUIRED=
OPEN_MUST=
