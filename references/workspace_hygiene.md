# Workspace Hygiene

## Goal

Prevent the agent from scattering files across the repository root.

Every created file should have a clear home, a predictable name, and a reason to exist.

## Placement Priority

Follow this order:

1. Existing project convention.
2. Existing folder for the artifact type.
3. A task-specific folder.
4. A general scratch/archive folder only when the output is temporary or exploratory.

Do not create new top-level folders when an existing suitable folder already exists.

## Root Directory Rule

Avoid adding files directly to the root unless one of these is true:

- The file is a standard project file, such as `README.md`, `LICENSE`, `.gitignore`, `package.json`, or `pyproject.toml`.
- The repository already expects that file at root.
- The user explicitly asked for it.

Examples of files that should usually not be placed at root:

- ad hoc notes
- analysis drafts
- temporary scripts
- command output logs
- screenshots
- generated reports
- one-off JSON or CSV exports
- test fixtures
- downloaded references

## Suggested Folders

Use project conventions first. If none exist, prefer:

- `docs/` for durable documentation.
- `docs/notes/` for working notes that should remain useful.
- `reports/` for analysis reports or generated summaries.
- `scripts/` for reusable scripts.
- `tools/` for developer utilities.
- `tests/fixtures/` for test fixtures.
- `artifacts/` for generated deliverables.
- `tmp/` or `.tmp/` for temporary files that should not be committed.
- `archive/` for old but intentionally retained outputs.

For projectless Codex workspaces, place scratch outputs under the workspace directory in a task-specific folder.

## Naming Rules

Prefer lowercase kebab-case:

```text
checkpoint-summary.md
top-anomalies.json
validate-outputs.ps1
git-conventional-commits.md
```

Use dates when files represent a time-specific snapshot:

```text
2026-06-01-checkpoint-summary.md
2026-06-01-validation-report.json
```

Use clear suffixes:

- `*-summary.md`
- `*-report.md`
- `*-anomalies.json`
- `*-validation.json`
- `*-notes.md`
- `*-draft.md`

Avoid vague names:

- `test.md`
- `output.txt`
- `new.py`
- `final2.md`
- `data.json`

## Archiving

Archive when an artifact is no longer current but may still be useful.

Prefer:

```text
archive/YYYY-MM-DD/<artifact-name>
```

For task-specific archive:

```text
archive/2026-06-01-agent-harness/<artifact-name>
```

Do not archive generated junk that has no future value. Delete it instead when safe.

## Commit Hygiene

Before committing, check whether generated or temporary files should be:

- committed as durable artifacts,
- moved into a better folder,
- added to `.gitignore`,
- deleted, or
- left untracked and mentioned to the user.

Do not commit scratch files unless they are intentionally part of the deliverable.

## Completion Report

When files were created or reorganized, report:

- Important files and their locations.
- Temporary files removed or left untracked.
- Any root-level files intentionally created and why.
