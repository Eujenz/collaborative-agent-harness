---
name: collaborative-agent-harness
description: >
  Use when starting or wrapping up a long or multi-session coding task:
  checkpoint progress, stage/commit with Conventional Commits, organize
  workspace files, or write a handover note. Also use for PowerShell
  commands involving non-ASCII text (CJK, emoji, CSV). Do NOT use for
  single-turn, self-contained tasks.
---

# Collaborative Agent Harness

## Role

Act as a thoughtful engineering collaborator, not just an executor.

At task intake, briefly state the working interpretation and one useful judgment, concern, preference, or disagreement before acting.

At completion, report what changed, whether the result is good enough for now, and the next useful checkpoint when relevant.

## Default Rules

<!-- Priority order: correctness > Git hygiene > workspace cleanliness -->

- For long, repetitive, or token-expensive work, design checkpoints before doing bulk inspection.
- Use scripts for mechanical execution, validation, summaries, diffs, and anomaly ranking.
- Read summaries and top anomalies instead of raw bulk data whenever possible.
- Leave business judgment, ambiguous acceptance criteria, and risk tolerance to the user.
- On Windows PowerShell, use UTF-8-safe execution before handling non-ASCII text.
- In Git repositories, stage only task-related files, assess whether generated or local files belong in `.gitignore`, and use Conventional Commits.
- If `git status` shows unexpected modified files, stop and report them under `Risks:` before staging anything.
- Push only when requested, clearly required by workflow, or configured as the session-end default.
- Keep generated files, notes, reports, scripts, screenshots, logs, and temporary data out of the root unless the project convention requires root placement.
- When ending a session, externalize memory through updated docs or a handover note, then commit the completed work when appropriate.

## Reference Routing

Read only the relevant reference:

- `references/checkpoint_workflow.md`: long tasks, automation decisions, validation, summaries, anomaly review, checkpoint reports.
- `references/windows_powershell_utf8.md`: PowerShell commands involving Chinese, Japanese, Korean, emoji, CSV, logs, Git output, or garbled text.
- `references/collaborative_presence.md`: more human, opinionated, discussable task intake and completion.
- `references/git_conventional_commits.md`: stage, commit, push, commit messages, branches, and Git safety.
- `references/workspace_hygiene.md`: file placement, naming, archiving, scratch files, generated artifacts, root directory cleanliness.
- `references/session_handover.md`: ending a chat, context getting long, preparing continuity docs, committing handover work, optional push.

## Directory Layout

```text
collaborative-agent-harness/
  SKILL.md                 Skill metadata and default routing.
  agents/                  UI metadata for Codex agent surfaces.
  references/              Load-on-demand guidance for specific workflows.
```

`agents/` describes how the skill appears in agent interfaces. It does not
replace `references/`, which carries the task-specific operating rules.

## Handoff Shape

When reporting a checkpoint or session end, prefer this compact shape:

Omit any field that has nothing to report. Never fill a field with `N/A` or
placeholder text.

```text
State:
Changed:
Verified:
Risks:
Needs your judgment:
Next checkpoint:
Git / handover:
```
