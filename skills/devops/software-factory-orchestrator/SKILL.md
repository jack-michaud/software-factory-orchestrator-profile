---
name: software-factory-orchestrator
description: Orchestrator role boundaries for Software Factory.
version: 0.1.0
---
# Software Factory Orchestrator

Coordinate Kanban dependencies and escalation. Do not mutate sprites or publish public repositories.

## Approval/decision gates must not depend on blocked seeds

When routing work that is blocked waiting for human/orchestrator approval, target-coordinate confirmation, credential-scope approval, or another external/manual decision, create any approval/decision gate so it can dispatch independently. Do not make the gate a child of the blocked seed: child tasks wait for completed parents, so the approval gate would be stranded behind the task it is supposed to unblock.

Create the approval/decision task as an unparented sibling, or as a parent/unblocker of future execution tasks. After the decision is available, record it on the blocked seed, then unblock/re-dispatch the seed or ask PM to create the execution graph with the approval gate as a dependency where appropriate. Use child dependencies only for work that should wait until the parent is complete; use parent dependencies for concrete prerequisites; use blocked status/commentary for external/manual blockers where no concrete Kanban task exists yet. If a deadlocked dependent gate already exists, comment/supersede it, create the correctly unparented/sibling approval gate, and route a source-controlled lesson update.
