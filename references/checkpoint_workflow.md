# Checkpoint Workflow

## Trigger

Use this workflow when a task has any of these properties:

- Many files, records, issues, logs, rows, or repeated checks
- High token cost if inspected manually
- Clear validation rules
- Long-running work that benefits from stopping points
- User business judgment is needed before continuing

## Workflow

1. Define one checkpoint goal and its boundary.
2. Record the current state needed to resume later.
3. Identify mechanical steps.
4. Decide whether a script is cheaper than manual agent inspection.
5. Write or adjust the script.
6. Run the script against the data.
7. Validate outputs mechanically where possible.
8. Read only the summary, failures, and top anomalies.
9. Ask the user only for decisions the agent cannot safely infer.
10. Record evidence, unresolved risks, and the next checkpoint.

## Harness Constraints

Each checkpoint should preserve five harness properties:

- **Instructions**: The agent knows which local docs, rules, scripts, or references govern this checkpoint.
- **State**: Progress, decisions, and open issues are written somewhere durable when the work may continue later.
- **Verification**: Completion is backed by runnable proof, generated summaries, checks, tests, or explicit evidence.
- **Scope**: The checkpoint has one bounded objective. Do not half-finish several unrelated objectives.
- **Lifecycle**: The checkpoint has a start state, execution path, wrap-up state, and clean restart path.

Use the repository or workspace as the source of truth. If future sessions need to know something, write it down instead of relying on chat memory.

## Lifecycle

At the start:

- Read the relevant local instructions or docs.
- Check current state, recent changes, and known unfinished work.
- Confirm the checkpoint boundary and definition of done.

During execution:

- Keep scope narrow.
- Prefer mechanical validation over confidence.
- Fix and rerun when verification fails.
- Record anomalies instead of hiding them.

At wrap-up:

- Update durable state or handover notes when continuation is likely.
- Record what was verified and what remains unverified.
- Commit only when the repo is safe to resume from.
- Leave the next checkpoint explicit.

## Automation Cost Test

Automate when at least two of these are true:

- The same operation repeats more than a few times.
- The raw input is larger than the useful conclusion.
- The check can be expressed as rules.
- The output can be summarized.
- The task may need to be rerun.
- The script will reduce future token use.

Avoid automation when:

- The task is tiny.
- The rules are still too ambiguous.
- The script would take longer than direct completion.
- Human judgment is the main work.

## Summary Format

Use this shape when reporting a checkpoint:

```text
Checkpoint:
- Scope:
- State updated:
- Automated:
- Verified:
- Top anomalies:
- Unverified:
- Human decision needed:
- My judgment:
- Next checkpoint:
```
