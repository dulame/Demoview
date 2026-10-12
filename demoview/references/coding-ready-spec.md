# Coding-Ready Spec

## Purpose

The final spec must be buildable by a coding agent without guessing product behavior. Every functional requirement should trace to approved or changed scenarios.

## Required Template

```md
# Demoview Spec: [Product or Feature Name]

## Objective
[What is being built, for whom, and why.]

## Scenario Review Summary
Approved: [IDs]
Changed: [IDs]
Denied: [IDs]
Excluded as unreviewed: [IDs]

## Source-of-Truth Scenarios
[Approved and changed scenarios only. Include final revised wording.]

## Non-Goals
[Denied scenarios and explicitly rejected behaviors.]

## Domain Model
Actors:
- ...

Entities:
- ...

States:
- ...

Permissions:
- ...

Canonical terms:
- ...

## Functional Requirements
| Requirement | Source scenarios |
|---|---|
| ... | S01, S03 |

## Interface Requirements
[Screens, commands, bot messages, API interactions, forms, or workflows depending on product type.]

## Data Requirements
[Data to store, relationships, lifecycle, retention, privacy constraints, and derived values.]

## Acceptance Criteria
| Criterion | Source scenarios |
|---|---|
| ... | S01 |

## Test Plan
[Scenario-based unit, integration, end-to-end, or manual checks.]

## Implementation Boundaries
Always:
- ...

Ask first:
- ...

Never:
- ...

## Open Questions
[Only questions that block implementation or materially affect scope.]
```

## Traceability Rule

If a requirement cannot point to an approved or changed scenario, either remove it or place it in Open Questions as a candidate.

## Tech Decisions

Prefer leaving tech stack unspecified unless:

- The user requested a stack.
- The existing repository clearly dictates a stack.
- The next phase explicitly asks for implementation planning.

When a tech assumption is necessary, label it as an assumption rather than a product requirement.
