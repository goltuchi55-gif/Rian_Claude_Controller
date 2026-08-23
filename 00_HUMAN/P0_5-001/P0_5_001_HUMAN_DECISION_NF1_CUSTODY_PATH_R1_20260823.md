---
document_id: P0_5_001_HUMAN_DECISION_NF1_CUSTODY_PATH_R1
document_type: HUMAN_DECISION
revision: 1
change_id: P0_5-001
phase: P0.5
issued_by: HUMAN_OWNER
source: HUMAN_OWNER_CHAT_APPROVAL
approval_at_jst: 2026-08-23T12:37:44+09:00
status: APPROVED
resolves: NF-1
resolves_audit: P0_5_001_HUMAN_RESOLUTION_CLOSURE_AUDIT_VERDICT_R1
resolves_audit_sha256: 716cf281812d33515ef6935c94e7af652340307a3ebc4f4c595a096d0b98a2bf
sidecar_required: true
---

# P0.5-001 HUMAN DECISION — NF-1 HUMAN DECISION CUSTODY PATH

## DECISION

Human Ownerは、`00_HUMAN/P0_5-001/` をP0.5におけるHuman Decision artifact専用のauthorized remote custody pathとして承認する。

この承認は、**Human Decision本体およびdetached SHA256 sidecarのcustody**に限定する。

## NOT AUTHORIZED BY THIS DECISION

`00_HUMAN/P0_5-001/` を次の用途に使用することは承認しない。

- Implementation source
- runtime state
- credential / secret
- Production deploy
- trading / financial execution
- 一般的なremote write path

## PRESERVATION / EFFECT BOUNDARY

- 既存の `P0_5_001_CONTROLLER_PHASE_DEFINITION_R1` は変更しない。本判断はR-04の改訂ではなく、NF-1に対するHuman-owned clarificationとして**追加記録**する。
- 既存Evidence、監査RAW、Verdictは変更しない。`P0_5_001_HUMAN_RESOLUTION_CLOSURE_AUDIT_VERDICT_R1` を含む既存監査artifactはimmutableのまま保持される。
- `P0_5_001_HUMAN_RESOLUTION_R1` の実体的内容（F-2 / F-5 / F-9 / F-10）は本判断によって変更されない。
- 本判断はNF-1のcustody path適法性のみを解決する。P0.5 closureの宣言およびP1開始は、Controllerが適用されるclosure/evidence checkを別途完了した後にのみ行われる。

## NON-EXTENSION RULE

今後同種のHuman Decision custody pathを新しいphase / changeへ**自動拡張してはならない**。

各phaseのauthorized envelopeを事前確認すること。本判断はP0.5（change_id `P0_5-001`）に限定して効力を持つ。

## SCOPE OF EFFECT ON NF-1

本判断は、closure audit verdict R1が提示した選択肢のうち **option 1**（`00_HUMAN/P0_5-001/` をauthorized P0.5 custody pathとして確認する）に該当する。R-04の列挙リスト改訂（option 2）は行わない。

Controllerは、この判断を踏まえてNF-1のclosure判定を行うこと。本artifact自体はNF-1のcloseを宣言しない。

## NON-AUTHORIZATION RESTATEMENT

本判断は、Production operation、credential / secret変更、financial / trading / order execution、force-push、history rewrite、canonical C1-C4 text modificationのいずれも承認しない。
