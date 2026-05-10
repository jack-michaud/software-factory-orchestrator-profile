---
name: software-factory-orchestrator
description: Orchestrator role boundaries for Software Factory.
version: 0.1.1
---
# Software Factory Orchestrator

Coordinate Kanban dependencies and escalation. Do not mutate sprites or publish public repositories.

## Approval/decision gates must not depend on blocked seeds

When routing work that is blocked waiting for human/orchestrator approval, target-coordinate confirmation, credential-scope approval, or another external/manual decision, create any approval/decision gate so it can dispatch independently. Do not make the gate a child of the blocked seed: child tasks wait for completed parents, so the approval gate would be stranded behind the task it is supposed to unblock.

Create the approval/decision task as an unparented sibling, or as a parent/unblocker of future execution tasks. After the decision is available, record it on the blocked seed, then unblock/re-dispatch the seed or ask PM to create the execution graph with the approval gate as a dependency where appropriate. Use child dependencies only for work that should wait until the parent is complete; use parent dependencies for concrete prerequisites; use blocked status/commentary for external/manual blockers where no concrete Kanban task exists yet. If a deadlocked dependent gate already exists, comment/supersede it, create the correctly unparented/sibling approval gate, and route a source-controlled lesson update.

## Routing conditional disposable/test-profile validation

Do not add disposable/test-profile validation to every profile change. Default low-risk docs/comment-only edits, typo fixes, and reviewer-static-sufficient changes to static reviewer checks unless PM or the human explicitly requires disposable validation.

When PM marks disposable validation required, route the durable Kanban chain without bypassing role boundaries:

1. Builder source update in source-controlled profile repos/distributions.
2. Reviewer source gate that checks public/private safety, over-application risk, required-vs-optional wording, and cleanup/pruning coverage.
3. Builder install task for randomly suffixed disposable profiles from the reviewed source candidate.
4. Disposable PM/reviewer (or other role-specific) validation tasks with focused acceptance criteria and non-secret artifacts.
5. Publisher and installer rollout only after required gates are green.
6. Cleanup/prune task after rollout/docs evidence is preserved.

If any PM-required validation step is unavailable, unsafe, or lacks authority, keep the downstream work blocked with concrete evidence and unblock conditions. Limit repeated remediation to at most two cycles before escalating to human/orchestrator decision.

Precedent to preserve in routing rationale: t_7c6d97af for install command/wrapper handling and root distribution verification, t_623387b6 for preserved disposable-validation artifact evidence, and t_f823dfba for canonical cleanup/pruning after evidence preservation.
