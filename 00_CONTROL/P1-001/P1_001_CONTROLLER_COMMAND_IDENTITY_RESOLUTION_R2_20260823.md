---
document_id: P1_001_CONTROLLER_COMMAND_IDENTITY_RESOLUTION_R2
document_type: CONTROLLER_CORRECTION
revision: 2
change_id: P1-001
phase: P1
issued_by: RIAN_CONTROLLER
issued_at_jst: 2026-08-23T13:34:00+09:00
status: FIXED
correction_scope: COMMAND_IDENTITY_ONLY
---

# P1-001 Controller Command Identity Resolution R2

## CONCLUSION

The authoritative P1 IMPLEMENTER command is:

`00_CONTROL/P1-001/P1_001_GRALPHA_IMPLEMENTATION_COMMAND_R1_READY.md`

SHA256:

`c69c213bc17d721f4dc6be47a49ad117d0ada4a9c926be2036c03672760a06f2`

This Git artifact is an exact-byte mirror of the already-active local command-of-record:

`C:\Projects\RIAN_CLAUDE_BRIDGE_P1_001_20260823\50_RIAN_CONTROLL\20260823_P1_001_GRALPHA_IMPLEMENTATION_COMMAND_R1_READY.md`

The local file was independently re-hashed and matches the same SHA256.

## NON-OPERATIVE DUPLICATE

`00_CONTROL/P1-001/P1_001_CONTROLLER_COMMAND_R1_20260823.md`
SHA256 `0a11a8254341f88baaf065b9842b49db13e87d0f076b03e8b485b7132fae5c04`

was issued after P1 local implementation had already begun from the authoritative command above.

It is therefore classified as a non-operative duplicate Controller artifact.

It MUST NOT:
- start a second Grα;
- supersede or broaden the authoritative command;
- publish implementation source to the public handoff repository;
- alter the active write/custody model;
- be used to infer additional P1 requirements.

The duplicate remains immutable history. Do not delete or rewrite it.

## EFFECT

- P1 remains ACTIVE.
- Existing Grα implementation continues from the authoritative command only.
- No new Human decision is required.
- P1 requirements, acceptance criteria, and non-waivable boundaries are unchanged.
- No second implementation stream is authorized.
- Next Controller action is to wait for the existing Grα BUILD_READY/result evidence, then verify custody before launching fresh Grβ independent audit.

This correction resolves command identity only and creates no authority expansion.
