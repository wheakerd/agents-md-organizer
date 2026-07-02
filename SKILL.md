---
name: agents-md-organizer
description: Use when creating, initializing, auditing, consolidating, or reorganizing repository AI instruction surfaces including AGENTS.md, CLAUDE.md, GEMINI.md, .cursor rules, codex/INDEX.md, task indexes, context routers, AI execution policy docs, and agent/workspace boundary docs. Use for context compression/compaction recovery, stale or legacy instruction context, durable project knowledge, latest-user-goal precedence, instruction sprawl, or unclear repo AI boundaries.
---

# AGENTS.md Organizer

## Overview

Create, audit, and reorganize repository instructions that AI agents can evaluate and follow reliably. Use `AGENTS.md` and routed context to preserve durable project knowledge, retire stale task memory, recover after context compression, and keep the latest user request as the active goal.

## Core Principle

Write every durable rule as an executable instruction:

| Rule quality | Requirement |
| --- | --- |
| Discoverable | The agent can find it from the stable entry file |
| Actionable | The rule says what to do, not only why it matters |
| Scoped | The rule says when it applies and when it does not |
| Ordered | The rule gives precedence when sources conflict |
| Evaluated | The rule says when to inspect live sources or ask |
| Verifiable | The rule defines what evidence closes the task |

Avoid motivational prose. Include rationale only when it changes agent behavior. Treat `AGENTS.md` as a startup index, not a project manual.

## Core Workflow

1. Classify the latest request: read-only audit, proposal-only, or write mode. In read-only/proposal mode, do not edit files; return findings and exact suggested wording. In write mode, change only the requested scope.
2. Restate the latest user goal, target instruction surfaces, write constraints, non-goals, and acceptance evidence. Treat this as the active task boundary unless the user changes it.
3. Locate candidate instruction surfaces with file listing/search first: `AGENTS.md`, tool-specific files, `.cursor/`, `codex/INDEX.md`, README, and docs only when linked by the entry file or required by the latest request. Do not read whole directories; classify candidates before opening leaf files.
4. Build a project boundary map when it is absent. Ask at most three neutral questions or propose conservative defaults for scope, protected areas, and verification sources.
5. Create an instruction inventory before reorganizing. For each retained, moved, quarantined, or removed item, record source, live evidence, classification, disposition, and unresolved doubts.
6. Put stable startup rules in `AGENTS.md`: entry order, precedence, scope limits, planning gates, write safety, user-choice triggers, context routing, compression recovery, and verification routing.
7. Move detailed context into indexed files when `AGENTS.md` would become a manual. Prefer `codex/INDEX.md` or an equivalent task router.
8. Give every route a reading order, eligible leaf files, excluded files, and a stop condition. Agents should load one primary route, then only task-needed leaf files.
9. Preserve durable knowledge, archive historical records only when explicitly useful, and quarantine stale, conflicting, or source-derivable task state. Do not copy or preserve secret values.
10. Verify with dry-run scenarios: startup-only orientation, one normal task route, one conflict or stale-context case, and one risky action requiring planning or user choice.

## Boundary Map Starter

When boundaries are missing, ask no more than three plain-language questions:

1. Which parts of the repo are in scope for this task, and which should stay off-limits?
2. Are there files, generated outputs, secrets, deploy steps, migrations, or external systems that require explicit approval?
3. What should prove the boundary and the finished result: tests, docs, owner files, CI, or specific paths?

If the user is unsure, offer this default: "I can start with a read-only inventory, treat generated/vendor/archive areas as off-limits, and verify against live code, config, and tests before suggesting edits."

Then restate the boundary map in five labels: In scope, Off-limits, Approval required, Verification sources, and Assumptions. Use plain path examples and say "This boundary is not yet explicit" for unknowns.

## Durability Boundary

Persist only instructions that a fresh agent should still obey in 30 days on an unrelated task.

| Surface | Belongs there |
| --- | --- |
| `AGENTS.md` | Stable startup rules, precedence, scope, safety gates, routing entry points, and verification expectations |
| Router/index files | Stable task-type routes, reading order, eligible leaf files, excluded files, and stop conditions |
| Leaf reference files | Durable repo-specific facts that are costly to infer, with source-of-truth and invalidation checks |
| Chat, task plan, PR, issue | Active objective, checklist, blockers, current branch, pending diffs, last-run results, handoff notes |
| Archive | Explicitly useful completed task logs, historical rollback or incident recovery records, historical rationale, and migration records; never default startup context |
| Quarantined | Stale, conflicting, source-derivable, secret-bearing, or unverified content that must not guide current work |

Preserve architecture decisions, domain vocabulary, public contracts, environment assumptions, operational constraints, and non-obvious gotchas only when still source-backed and useful across future tasks. For each durable fact, name the source of truth or verifying command, when it must be rechecked, and the file that owns it.

Before calling instruction knowledge durable or version-controlled, verify `AGENTS.md`, routers, and retained leaf files are tracked and not ignored. If they are untracked, ignored, or no VCS exists, report that risk and ask whether to add/init VCS or keep proposal-only.

## AGENTS.md Shape

Use durable sections with imperative rules:

| Section | Defines |
| --- | --- |
| Start Here | Required first reads and router location |
| Latest Request Rule | Do not record current task state here; state only that the latest direct user request in chat defines the active goal, while repo docs provide standing rules and background |
| Precedence | Platform/tool instructions, latest user request, shared `AGENTS.md` policy, tool-specific deltas, scoped routers/leaf files, then historical notes |
| Scope Rules | Included paths, excluded paths, generated/vendor dirs, protected files, external systems, delete/write/deploy/migration limits, secret/data handling, and source-of-truth rules |
| Durable Knowledge | Stable repo-specific facts worth versioning, with source-of-truth and invalidation checks |
| Multi-Agent Surfaces | Canonical file, mirrors, and tool-specific deltas for `AGENTS.md`, `CLAUDE.md`, `GEMINI.md`, `.cursor/`, and similar files |
| Planning Gate | Changes requiring confirmation before writes |
| Context Loading | How to avoid reading everything |
| Delegation | When subagents are allowed or required |
| Workspace Safety | Dirty worktree, branch/worktree, no-VCS behavior |
| Resume/Compression | How to reload source-of-truth files after context loss |
| Context Freshness | Labels and stop rules for Current, Reference, Archive, and Quarantined content |
| User Choice | When to present options instead of proceeding |
| Verification | Required checks and evidence to report |

Treat `AGENTS.md` as a startup index. Aim for 60-120 lines, 3-7 bullets per section, and bullets shaped as trigger -> action -> evidence. Move command catalogs, long rationale, repo facts, and domain details into routed files.

## Precedence Rules

Use this order for new or revised instructions. A repository may add stricter safety gates only inside lower-priority repo-local sources; it must not outrank platform/tool instructions or the latest direct user request:

1. Platform and tool instructions.
2. Latest direct user request for the current task.
3. Shared repository policy in `AGENTS.md`.
4. Tool-specific execution deltas in `CLAUDE.md`, `GEMINI.md`, `.cursor/`, or similar files.
5. Router and leaf files within their delegated scope.
6. Prior plans, summaries, archives, and chat-derived notes only as historical hints.

Live source, config, tests, and git/workspace state are authoritative for facts and current state. They invalidate stale docs, but they do not silently override explicit policy. If policy and live state cannot both be satisfied, state the conflict and present options.

## Evaluative Compliance

Do not encode blind obedience. Rules should tell agents how to decide:

| Situation | Agent behavior |
| --- | --- |
| Rule is clear and current | Follow it directly |
| Rule conflicts with latest request or live state | State conflict, inspect source of truth, then proceed from precedence |
| Latest user request conflicts with repo docs | Follow the latest request within platform/tool safety limits; note the stale or conflicting doc; update, quarantine, or report it according to the requested mode |
| Request is broad, vague, or boundary-light | Convert it into 2-3 concrete options with a recommended default and tradeoff |
| User cannot answer boundary questions | Proceed only with read-only audit or the narrowest reversible change, then state assumptions |
| Rule requires tradeoff or irreversible action | Present 2-3 concrete options and wait for user choice |
| Rule is missing for a risky action | Ask for policy or propose a narrow safety plan |

Irreversible actions include deleting or moving instruction files, removing archives, `rm`, `git reset`, `git restore`, `git clean`, rewriting history, force-pushes, deploys, migrations, mutating external systems, changing ignore rules that expose files, rotating or removing credentials, and bulk reorganizations.

Use non-blaming escalation language: "The repo gives mixed signals" or "This boundary is not yet explicit", not "you did not specify" or "the docs are wrong."

Default option ladder:

1. Read-only inventory and proposed wording.
2. Narrow reversible edit inside the agreed scope.
3. Broader reorganization plan with files to move or quarantine and confirmation before writes.

For irreversible actions, show impact, rollback path if any, and wait for choice.

## Workspace Safety

Before edits, inspect VCS/workspace state. If files are dirty or untracked, distinguish existing user changes from agent changes, do not revert unrelated work, and avoid overwriting modified files without approval. If no VCS exists, default to proposal-only; proceed with writes only after the user approves the affected files, expected changes, and rollback or backup plan.

For secrets, do not copy, preserve, or quote the secret value. Report the path and secret type without exposing contents, recommend rotation, and remove or redact only with explicit approval.

Do not add secret-bearing files such as `.env` files, credential stores, private keys, production config dumps, or exported data with tokens to startup or router reading orders. Document only variable names, secret types, owners, and approved validation commands.

## Router Shape

A router must map task type to minimal reading order. Useful groups include project overview, architecture, domains, API/routes, operations, verification, context governance, and archive.

Every route should answer:

1. Which index file should be read next?
2. Which leaf files are eligible for this task?
3. Which files must not be used for current-task orientation?
4. When should the agent stop reading and inspect live source instead?

Label routed files as Current, Reference, Archive, or Quarantined. Current means durable, currently valid repo guidance only; it must not contain active task goals, checklists, branches, blockers, handoff notes, or last-run results. Reference requires live-source checking. Archive is only for history, cleanup, migration, deletion, or explicit user request. Quarantined content must not guide current work.

Archive routes must be opt-in. Do not include archive, recovery, completed-task logs, or chat transcripts in Start Here, default project overview, or implementation routes. Route to them only when the latest user request explicitly asks for history, cleanup, migration, deletion, rollback/incident recovery, or archived-history recovery.

Resume/context-compression recovery must reload only Current startup/routing sources unless the latest user request explicitly asks for archived history.

Avoid routes that say to read an entire directory unless the task is explicitly an audit, migration, or documentation cleanup.

### Example Router Entry

Task: API route change
Read: `AGENTS.md` -> `codex/INDEX.md` -> owning route file -> eligible API leaf only if the route or live source indicates API behavior changes.
Eligible leaves: auth notes only if auth behavior changes.
Do not read: `archive/`, completed task logs, old migration notes.
Stop: once the owning module and verification command are identified; inspect live source next.

## Resume and Compression Recovery

On resume or after context compaction:

1. Reload `AGENTS.md`, then the router/index named there; reselect the route from the latest user goal before reading leaf files.
2. Restate the latest user goal, requested scope, and acceptance evidence.
3. Inspect git/workspace state and live source before trusting summaries.
4. Treat prior plans, status notes, and archives as hints until verified.

## Policy Extraction

When importing ideas from another repository, extract reusable behavior and leave local facts behind. Branch prefixes, runtime aliases, DB commands, service names, ignored files, and verification commands belong in that repository's docs unless they apply everywhere.

## Compliance Check

Before finishing, inspect the generated instructions as if no chat context exists:

| Check | Pass condition |
| --- | --- |
| Startup | Agent knows the first file and next router |
| Conflict | Agent knows which source wins |
| Scope | Agent knows what not to touch |
| Planning | Agent knows when to stop for approval |
| Choice | Agent knows when to present options |
| Context | Agent avoids broad or stale reading |
| Verification | Agent knows required checks before claiming done |

For each dry run, list files read in order, stop condition, source-of-truth decision, required checks, and pass/fail result.

Completion evidence must include changed instruction surfaces, router paths added or removed, durable knowledge preserved, stale/task-state material quarantined or removed, live sources inspected, verification scenarios run, remaining risks, and exact checks future agents must run before claiming done.

## Final Deliverables

For read-only or proposal tasks, return findings by severity with file/section, why it matters, exact suggested wording, assumptions, and verification/read scope. State that no files were edited.

For implementation tasks, return:

- Files created or changed, with one-line purpose for each.
- Concise summary of `AGENTS.md` or router behavior changed.
- User decisions still required, as 2-3 concrete options.
- Verification evidence: entry path simulated, routes tested, checks run, and checks not run.

Do not restate the full generated instructions unless the user asks.

## Common Mistakes

| Mistake | Correction |
| --- | --- |
| Writing explanatory prose first | Write executable agent instructions first |
| Blindly following stale notes | Evaluate against latest request and live sources |
| Turning AGENTS into a full manual | Keep entry short; route details elsewhere |
| Using vague policy language | Convert it to triggers, actions, and stop conditions |
| Preserving old task state | Keep current goals in chat, not durable startup docs |
| Mixing source facts with notes | Prefer live code, schema, config, and routes |
| Creating a router without stop rules | Tell agents exactly when enough context is loaded |
| Letting archive guide current work | Make archive routes opt-in and non-authoritative |
