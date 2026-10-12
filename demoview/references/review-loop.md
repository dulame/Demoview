# Review Loop

## Goal

Convert one scenario at a time into evidence. The user should make one lightweight decision, not review a requirements batch.

## Prompt Shape

After presenting one scenario, ask for review in this form:

```md
For S01, reply with one decision:
- approve
- deny
- change: ask for phone number before confirmation
```

Stop after this prompt. Do not include another unreviewed scenario in the same response.

## Handling Feedback

| User response | Action |
|---|---|
| Approves a scenario | Mark it Approved and keep wording stable. |
| Denies a scenario | Mark it Denied and capture the rejected behavior as a non-goal. |
| Changes a scenario | Rewrite the scenario, mark it Changed, and preserve the user's correction. |
| Gives a broad correction | Apply it to the current and future scenarios; show only the revised current scenario for confirmation. |
| Adds a new behavior | Create a new scenario ID and ask for review. |

After recording a decision, either present one next scenario or ask one focused question that is necessary to create it. Never leave two scenarios awaiting review.

## When To Stop Reviewing

Stop generating scenarios and move to extraction when:

- The primary user goals have approved or changed scenarios.
- Major permission boundaries are covered.
- At least one empty, invalid, or failure path is covered for risky flows.
- Remaining open questions are specific enough to list in the spec.

If the user explicitly says to proceed with partial review, keep unreviewed material out of requirements and list the risk.

## Review Summary

Before writing the spec, summarize:

```md
Approved: S01, S03, S04
Changed: S02, S05
Denied: S06
Unreviewed, excluded from requirements: S07, S08
Blocking questions: none
```
