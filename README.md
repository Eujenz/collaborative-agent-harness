# Collaborative Agent Harness

Collaborative Agent Harness is a Codex skill for making coding agents work with more continuity, restraint, and judgment.

It is not a domain-specific development skill. It is a small operating harness for how an agent should work: when to checkpoint, when to script, when to summarize, when to ask for human judgment, how to keep Git clean, how to avoid workspace clutter, and how to leave a handover for the next chat.

## Quickstart

Install this repository as a Codex skill by copying it into your Codex skills directory:

```powershell
Copy-Item -Recurse collaborative-agent-harness $env:USERPROFILE\.codex\skills\collaborative-agent-harness
```

The skill is activated by its metadata in `SKILL.md`. Once installed, Codex can use it when a task involves long-running work, checkpoints, automation, Git commits, workspace organization, PowerShell UTF-8 issues, or session handover.

## How It Works

The skill keeps the main `SKILL.md` short. It acts as a router: the agent reads the entry rules first, then opens only the reference file that matches the situation.

The core behavior is:

1. Treat the user as the business decision maker.
2. Use scripts for mechanical and repeatable work.
3. Read summaries and top anomalies instead of raw bulk data.
4. Keep Git commits focused and conventional.
5. Keep generated files out of the repository root.
6. Preserve continuity with handover notes when a session ends.

## Basic Workflow

1. **Intake** - The agent briefly states its interpretation and one useful judgment, concern, preference, or disagreement.
2. **Checkpoint design** - For large work, the agent decides what can be automated, validated, summarized, and deferred to human judgment.
3. **Scripted execution** - Mechanical work is delegated to scripts when that is cheaper or more reliable than token-heavy inspection.
4. **Anomaly review** - The agent reads summaries, failures, and top anomalies rather than entire raw outputs.
5. **Git and workspace hygiene** - The agent stages only task-related files, assesses `.gitignore`, writes Conventional Commits, and avoids root clutter.
6. **Session handover** - When wrapping up, the agent updates durable docs or writes a handover note so the next conversation can resume cleanly.

## What's Inside

### Skill Entry Point

- `SKILL.md` - Short trigger and routing rules for the harness.

### References

- `references/checkpoint_workflow.md` - Automation decisions, validation, summaries, anomaly review, and checkpoint reporting.
- `references/collaborative_presence.md` - A more human, opinionated, discussable agent style.
- `references/git_conventional_commits.md` - Safe stage, commit, push, `.gitignore` assessment, and Conventional Commits.
- `references/session_handover.md` - End-of-session handover notes, continuity docs, commits, and optional push.
- `references/windows_powershell_utf8.md` - UTF-8-safe PowerShell execution for non-ASCII text.
- `references/workspace_hygiene.md` - File placement, naming, archiving, scratch files, and root directory cleanliness.

## Philosophy

- **Harness before heroics** - Design the workflow before spending tokens on bulk inspection.
- **Scripts for repetition** - Let deterministic tools do mechanical work.
- **Summaries over sprawl** - Bring only the useful signal back into context.
- **Human judgment stays human** - Business priority, ambiguity, and risk tolerance belong with the user.
- **Continuity is externalized** - Handover notes and commit history compensate for limited agent memory.
- **The workspace matters** - A completed task should not leave a mess behind.

## Current Status

This is a personal Codex skill, tuned for a Windows and GitHub workflow. It is intentionally small and modular so the entry skill stays lightweight while detailed behavior lives in reference files.
