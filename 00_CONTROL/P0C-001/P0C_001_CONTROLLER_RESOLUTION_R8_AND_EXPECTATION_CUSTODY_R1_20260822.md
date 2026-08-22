---
document_id: P0C_001_CONTROLLER_RESOLUTION_R8_AND_EXPECTATION_CUSTODY
document_type: CONTROLLER_RESOLUTION
revision: 1
change_id: P0C-001
issued_by: RIAN_CONTROLLER
status: ACTIVE_FOR_CURRENT_GATE
scope: PRIMARY_AUDIT_EXPECTATION_CUSTODY_ONLY
creates_no_production_authority: true
creates_no_canonical_write_authority: true
---

# P0-C-001 Controller Resolution — R8 authority and Expectation custody

## AUTHORITY RESOLUTION

Existing Human-issued R8 authority already establishes:

- C1 = AUTHORIZED_CANONICAL_COPY_VIA_GIT
- C2 = AUTHORIZED_CANONICAL_COPY_VIA_GIT
- C3 = AUTHORIZED_CANONICAL_COPY_VIA_GIT
- C4 = AUTHORIZED_CANONICAL_COPY_VIA_GIT
- OPERATING_PROFILE_LITE = INCLUDED_IN_C1 / AUTHORIZED_FOR_GOVERNING_USE

A Git read/use copy has governing authority when its measured SHA256 exactly matches the activated canonical identity.
Absence of the old local canonical root by itself does not revoke that Human-issued authority.

Therefore the Primary Auditor's reported OPEN_MUST concerning
`C:\Projects\Claude_Development_Platform_Lite` being absent is RESOLVED_BY_EXISTING_HUMAN_AUTHORITY,
subject to exact digest matching of the Git reference copies used by the audit.

This resolution does not waive the P0-C requirement to independently verify the full activated 9-document set before PASS.

## EXPECTATION CUSTODY

Primary Auditor reported expectation SHA256:

`fc473adc3176f4d578f1892ad56d1da9b84cba005a828b13e05fff0cb9bb6976`

Controller has not yet independently re-hashed the exact expectation bytes.
Do not open any audit target yet.

Primary Auditor shall:

1. Keep the expectation bytes unchanged.
2. Keep the detached sidecar unchanged.
3. Push the exact expectation file and sidecar only to:
   `goltuchi55-gif/Rian_Claude_Controller`
4. Use path:
   `05_EVIDENCE/P0C-001/PRIMARY_AUDIT/CUSTODY_PENDING/`
5. Do not open `10_ALPHA`, `20_BETA`, `30_GAMMA`, or the RIAN consolidated candidate.
6. Return only the commit SHA and pushed paths.
7. STOP at the custody checkpoint.

RIAN Controller will then independently fetch and hash the exact Git bytes.
If SHA256 equals the reported value, Controller will record the seal acknowledgement and release the artifact-disclosure gate.

## CURRENT GATE

- R8 canonical Git authority: RESOLVED
- local canonical-root absence: NOT A BLOCKER
- expectation content authored: YES
- expectation exact-byte Controller re-hash: PENDING
- audit target disclosure: LOCKED
- Human approval: LOCKED
