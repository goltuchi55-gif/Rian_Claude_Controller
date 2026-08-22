---
document_id: P0C_001_HUMAN_DECISION_STOP_POLICY
document_type: HUMAN_DECISION
change_id: P0C-001
status: ACTIVE
decided_by: HUMAN_OWNER
effective_at: 2026-08-22T18:54:00+09:00
scope: P0C-001_AND_RIAN_CLAUDE_BRIDGE_CURRENT_WORKFLOW
---

# P0-C-001 Human Decision — STOP Policy

## HUMAN DECISION

Human Owner decision:

「こちらへの承認行為、あと金銭にかかわるソフトの改造以外であれば、特にSTOPは設けない。」

## OPERATIVE INTERPRETATION

1. RIAN shall not add discretionary or precautionary STOP points beyond the ACTIVE canonical rules and this Human Decision.
2. Ordinary in-scope work proceeds without returning to the Human Owner merely for permission. This includes read-only investigation, governance verification, drafting, local candidate work, testing, evidence creation, permitted Git handoff writes, and audit execution within an already authorized scope.
3. A STOP / Human return remains required when an explicit Human Owner approval or Human Gate is required by the ACTIVE canonical set, the current COMMAND, or an already-recorded Human Decision.
4. A STOP / Human return is additionally required for modification of software or systems that is materially related to money, monetary execution, payment, trading execution, or other direct financial effect.
5. This decision does not itself authorize Production changes, runtime changes, credential changes, canonical-text changes, or any other action that separately requires Human approval under the ACTIVE canonical set. Such cases are treated under item 3.
6. This decision does not shrink, delete, or reinterpret any ACTIVE C1-C4 MUST. Its purpose is to eliminate AI-invented approval loops and unnecessary STOPs.

## DEFAULT

If work is inside the already authorized scope and no explicit Human approval/Human Gate or money-related software modification is triggered, proceed.

If one of those triggers is reached, stop once, present the minimum decision required, and wait for the Human Owner.
