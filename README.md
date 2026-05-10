# softwarefactoryorchestrator profile

This is a local-installable role distribution root for current Hermes. It is generated/maintained from the Software Factory profiles monorepo prototype.

Install locally for testing:

```bash
hermes profile install /path/to/software-factory-profiles/profiles/orchestrator --name softwarefactoryorchestrator-monorepo-test --yes
```

Role boundary: Coordinates durable Kanban task flow and dependencies without performing infrastructure mutation.

## Generated public repository shape

This root is current-Hermes-compatible: `distribution.yaml` is at repository root.

Install after publication:

```bash
hermes profile install https://github.com/jack-michaud/software-factory-orchestrator-profile.git --name softwarefactoryorchestrator
```

Update after publication:

```bash
hermes profile update softwarefactoryorchestrator --yes
```

Public/private boundary: credentials, runtime state, logs, memories, sessions, Kanban DB/workspaces, sprite credentials, SSH keys, OAuth tokens, API keys, and private Obsidian notes are not included.

## Runtime configuration

This distribution owns `config.yaml`. The file pins model execution to `gpt-5.5` via provider `openai-codex` using `chat_completions`, enables the public-safe `hermes-cli` toolset, and points `skills.external_dirs` at `../../skills` so controlled installs can reuse shared skill overlays without vendoring private/local skill trees.

Authority for this role is governed by `SOUL.md` plus the role-specific bootstrap skill. Publisher/docs profiles additionally include `role-capability-manifest.yaml`.

## Publication provenance

Version: v0.1.0
Source of truth: https://github.com/jack-michaud/software-factory
Source tag: profiles/v0.1.0
Source commit: 63035a90746ab304b7e8c5f231d9d89c2106e9d8
Generated manifest: GENERATED_METADATA.json
License: MPL-2.0

This repository is generated. File issues and feature requests on https://github.com/jack-michaud/software-factory rather than editing this generated repository directly.
