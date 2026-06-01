# Git Autonomy and Conventional Commits

## Goal

Help a user who is still learning Git by safely handling routine stage, commit, and push operations.

The agent may act autonomously, but must avoid mixing unrelated work into commits.

## Safety Rules

Before staging:

```powershell
git status --short
git branch --show-current
```

Stage only files related to the completed task. If unrelated modified files exist, leave them unstaged and mention them.

Before staging untracked files, assess whether they should be committed, moved, deleted, or ignored.

Consider adding files to `.gitignore` when they are:

- local environment files, such as `.env`, `.env.local`, or machine-specific config
- credentials, tokens, keys, certificates, or secret-bearing files
- dependency folders, such as `node_modules/`, `.venv/`, or vendor caches not owned by the repo
- build outputs, such as `dist/`, `build/`, `out/`, `target/`, or compiled binaries
- tool caches, such as `.pytest_cache/`, `.mypy_cache/`, `.ruff_cache/`, or `.next/`
- logs, temporary files, scratch outputs, local reports, or generated artifacts that are not durable deliverables
- OS/editor files, such as `.DS_Store`, `Thumbs.db`, or `.vscode/` when not intentionally shared

Do not add files to `.gitignore` blindly. First check existing project conventions and whether the file is a real deliverable.

If a generated artifact is useful to keep but not source-controlled, move it to an appropriate ignored folder such as `tmp/`, `.tmp/`, or a project-specific artifacts directory.

If `.gitignore` is changed, include the reason in the commit or completion report.

Before committing:

```powershell
git diff --cached --stat
git diff --cached
```

Do not commit if:

- The staged diff includes unrelated user work.
- The working tree contains conflicts.
- The change has not been verified when verification is practical.
- The commit would include secrets, credentials, generated junk, or local-only config.
- Untracked files have not been classified as commit, ignore, archive, or delete.

Push only when:

- The user explicitly asks to push.
- The user asks the agent to submit the work.
- The current workflow clearly requires pushing the branch.

Before pushing:

```powershell
git remote -v
git status --short --branch
```

Prefer:

```powershell
git push
```

If the branch has no upstream, use:

```powershell
git push -u origin <branch>
```

## Commit Message Format

Use Conventional Commits 1.0.0:

```text
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

The description must immediately follow the colon and space.

Use lowercase types consistently.

## Common Types

Use:

- `feat`: adds a user-facing or application feature.
- `fix`: patches a bug.
- `docs`: documentation-only changes.
- `test`: adds or updates tests.
- `refactor`: code change that neither fixes a bug nor adds a feature.
- `perf`: performance improvement.
- `style`: formatting-only change with no behavior change.
- `build`: build system or dependency changes.
- `ci`: CI configuration changes.
- `chore`: maintenance that does not fit another type.
- `revert`: reverts prior commits.

## Scope

Add a scope when it clarifies the affected area:

```text
feat(parser): add array parsing
fix(api): handle missing token
docs(skill): explain checkpoint workflow
```

Keep the scope short and noun-like.

## Breaking Changes

Use `!` before the colon or a `BREAKING CHANGE:` footer.

Examples:

```text
feat(api)!: remove legacy auth parameter
```

```text
feat: change config inheritance

BREAKING CHANGE: `extends` now resolves relative to the config file.
```

`BREAKING CHANGE` must be uppercase when used as a footer token.

## Choosing the Commit Shape

Prefer one focused commit per logical change.

If changes cover multiple unrelated purposes, split commits when practical.

For small routine commits, use only a subject line:

```text
docs: update agent harness skill
```

Use a body when the "why" is not obvious:

```text
fix: prevent stale summary reuse

Regenerate the checkpoint summary after validation so the agent does not
read anomalies from a previous run.
```

Use footers for references:

```text
fix: prevent request race

Refs: #123
```

## Agent Completion Report

After committing or pushing, report:

- Commit hash
- Commit message
- Branch
- Whether push succeeded
- Any files intentionally left unstaged
