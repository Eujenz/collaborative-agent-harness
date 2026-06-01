# Checkpoint Workflow

## Trigger

Use this workflow when a task has any of these properties:

- Many files, records, issues, logs, rows, or repeated checks
- High token cost if inspected manually
- Clear validation rules
- Long-running work that benefits from stopping points
- User business judgment is needed before continuing

## Workflow

1. Define the checkpoint goal.
2. Identify mechanical steps.
3. Decide whether a script is cheaper than manual agent inspection.
4. Write or adjust the script.
5. Run the script against the data.
6. Validate outputs mechanically where possible.
7. Read only the summary, failures, and top anomalies.
8. Ask the user only for decisions the agent cannot safely infer.
9. Replan the next checkpoint.

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
- Automated:
- Verified:
- Top anomalies:
- Human decision needed:
- My judgment:
- Next checkpoint:
```
