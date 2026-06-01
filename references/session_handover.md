# Session Handover

## Goal

Because agents do not have reliable long-term memory and future chats may start with limited context, preserve continuity in repository artifacts before ending a session.

The handover should let a future agent understand:

- What was being done
- What changed
- Why decisions were made
- What remains
- How to verify or continue

## Trigger Phrases

Use this workflow when the user says or implies:

- "handover"
- "checkpoint"
- "wrap up"
- "stop here"
- ending the session
- wrapping up the work
- continue next time
- prepare for the next chat
- summarize for the next agent

Also use it when context is getting long and continuity matters.

## Handover Location

Follow existing project conventions first.

If none exist, prefer:

```text
docs/handover/YYYY-MM-DD-<task>.md
```

If `docs/handover/` feels too formal for the project, use:

```text
docs/notes/YYYY-MM-DD-<task>-handover.md
```

For projectless Codex workspaces, create a task-specific handover inside the workspace rather than the user home directory.

## Handover Content

Use this structure:

```markdown
# Handover: <task name>

## Current State

Briefly describe what the session accomplished and where the work stands.

## Decisions

List important decisions and why they were made.

## Files Changed

List relevant files and what changed in each.

## Verification

Record commands, checks, tests, or review performed.

## Open Risks

List known issues, uncertainty, or things not verified.

## Next Steps

Give concrete next actions for the next agent or user.
```

Keep the handover concise. It is a resume point, not a full transcript.

## Docs Update Rule

Before creating a new handover file, check whether an existing durable doc should be updated instead:

- `README.md`
- `docs/README.md`
- `docs/architecture.md`
- `docs/workflow.md`
- existing task notes
- existing handover notes

Prefer updating the most relevant existing doc when the information is durable.

Create a handover note when the information is session-specific.

## Git Rule

At session end in a Git repository:

1. Check `git status --short`.
2. Ensure docs and handover files are in sensible locations.
3. Stage only related files.
4. Review the staged diff.
5. Commit using Conventional Commits.
6. Push only when allowed by the session's push policy.

Recommended commit messages:

```text
docs(handover): record session state
docs(skill): add session handover workflow
chore: checkpoint current work
```

Use `docs(...)` when the main change is documentation or handover notes.

Use `chore` only when committing a mixed checkpoint that does not fit a better type.

## Push Policy

Default push behavior is conservative:

- Push if the user explicitly asked.
- Push if the user says session-end push is the default.
- Push if remote continuity is required for the next environment or collaborator.

Otherwise, commit locally and report that push was not performed.

If pushing, report:

- Branch
- Remote
- Whether upstream was set
- Push result

## Completion Report

After handover, report:

- Handover doc path
- Commit hash and message
- Branch
- Push status
- Important uncommitted or unstaged files, if any
- Recommended next checkpoint
