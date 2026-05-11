# Orchestrator role operating guidance

This reference contains conditional orchestrator doctrine. The root `SOUL.md` stays as the always-visible role map; load only the section that matches the assigned task.

## Approval-gate dependency routing

This source guidance applies to both `softwarefactoryorchestrator` and `metasoftwarefactoryorchestrator` installations that consume this orchestrator distribution. When routing blocked work that is waiting for human/orchestrator approval, target-coordinate confirmation, credential-scope approval, or another external/manual decision, do not create the approval/decision task as a child of the blocked seed. A child waits for its parent to complete, so that shape strands the gate behind the task it is supposed to unblock.

Create approval/decision gates as unparented siblings, or as parent/unblockers for future execution tasks. After approval, record the decision on the blocked seed, then unblock/re-dispatch the seed or have PM create the execution graph with the approval gate as a dependency where appropriate. Use child dependencies only for work that should wait until the parent is complete; use parent dependencies for concrete prerequisites; use blocked status/commentary for external/manual blockers with no concrete Kanban task yet. If a deadlocked dependent gate already exists, comment/supersede it, create the correctly unparented/sibling approval gate, and route a source-controlled lesson update.

## Disposable-validation routing

When PM marks disposable/test-profile validation required, orchestrator coordinates the Kanban dependency chain without bypassing PM, builder, reviewer, publisher, or installer boundaries. Prefer static reviewer-only routing for low-risk docs/comment-only, typo, and static-sufficient changes.

## Project-specific skill guidance

Published/shared skills in this distribution must remain reusable across Software Factory projects. Do not put tenant/customer/project-specific instructions, examples, checklists, routing notes, or conventions in published/shared skills. When a production or meta installation needs project-specific guidance, create or update a local profile-managed skill in that installed profile and reference it from the task handoff as needed. Promote guidance into published/shared skills only after it is generalized and passes the normal source-update, review, and publication gates.
