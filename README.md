# AGENTS.md Organizer

Codex skill for creating, auditing, and reorganizing repository AI instruction boundaries.

Use this skill when a project needs durable, version-controlled AI instructions such as `AGENTS.md`, `CLAUDE.md`, `GEMINI.md`, `.cursor` rules, or context routers. It helps agents keep the latest user request primary, recover after context compression, preserve long-term project knowledge, and keep stale task context out of startup paths.

## What It Helps With

- Define clear repository boundaries for AI agents.
- Convert vague project rules into executable instructions.
- Separate durable project knowledge from active task state.
- Route large context through indexes with explicit stop conditions.
- Quarantine stale, conflicting, source-derivable, or secret-bearing notes.
- Require verification evidence before claiming work is complete.

## Install

Clone this repository into your Codex skills directory:

```bash
git clone https://github.com/wheakerd/agents-md-organizer.git ~/.codex/skills/agents-md-organizer
```

Then invoke it as:

```text
Use $agents-md-organizer to audit this repo's AGENTS.md and context routers.
```

## Skill Contents

```text
agents-md-organizer/
├── SKILL.md
└── agents/
    └── openai.yaml
```

`SKILL.md` contains the executable workflow for building AI instruction boundaries. `agents/openai.yaml` provides the UI-facing display name, description, and default prompt.

## Repository Description

Suggested GitHub description:

```text
Codex skill for organizing AGENTS.md and repository AI instruction boundaries.
```

## License

MIT
