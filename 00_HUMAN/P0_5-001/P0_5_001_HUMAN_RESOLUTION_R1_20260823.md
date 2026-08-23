---
document_id: P0_5_001_HUMAN_RESOLUTION_R1
document_type: HUMAN_DECISION
revision: 1
change_id: P0_5-001
phase: P0.5
issued_by: HUMAN_OWNER
approved_at_jst: 2026-08-23T11:57:04+09:00
status: APPROVED
source: HUMAN_OWNER_CHAT_APPROVAL
sidecar_required: true
---

# P0.5-001 HUMAN RESOLUTION

**F-2:** R8 Human authorityを再確認し、activated canonical identityとSHA256が一致するGit read/use copyをgoverning authorityとして採用する。

**F-5:** P0.5のremote custody実績は、完成済みLOCAL_CUSTODY_RELAYではなく、R-05で暫定許可されたclean-clone/bootstrap custodyとして認定する。過去Evidenceは変更しない。P1でsingle-emitter custody relayをMUST実装する。

**F-9:** remote Gitの運用上のrestore routeはrevert/corrective commitによるsupersedeとする。既に公開されたhistorical bytesの完全撤回は保証不能であることを既知残存リスクとして受容する。force-push/history rewriteは使用しない。

**F-10:** `goltuchi55-gif/Rian_Claude_Controller`をNON-PRODUCTION Control/Handoff/Evidence/Historian repositoryとして分類する。Git操作自体をProduction deployとは扱わず、Production runtime/state/credential/trading execution用途には使用しない。

## PRESERVATION / EFFECT BOUNDARY

- Secondary RAW findings and Secondary Verdict R1 remain immutable and are not rewritten by this Human Decision.
- This Human Decision resolves the Human-owned questions above; Controller must still perform the applicable closure/evidence check before declaring P0.5 closed or starting P1.
- No Production operation, credential/secret change, financial/trading/order execution, force-push, history rewrite, or canonical C1-C4 text modification is authorized by this decision.