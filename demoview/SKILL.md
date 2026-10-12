---
name: demoview
description: "Use when a rough product idea, feature request, or vague spec must become a coding-ready spec, especially when requirements are unclear, product behavior needs examples, or stakeholders need to approve concrete behavior before build."
---

# Demoview

## Overview

Demoview turns fuzzy product intent into a coding-ready spec through a guided design conversation and concrete behavioral scenarios. The core bet: people often cannot describe the whole product upfront, but they can shape a plan step by step and recognize whether one specific demo feels right.

## Hard Gate

Do not generate scenarios directly from a rough idea. First use `brainstorming` to establish shared understanding, ask one focused question per response, and get approval for a compact design brief or general plan.

After planning approval, present exactly one scenario per response and get the user to approve, deny, or change it. Keep at most one unreviewed scenario active. Do not write the coding-ready spec until enough scenarios have been reviewed.

Scenario status is the source of truth:

| Status | Meaning |
|---|---|
| Approved | Build this behavior. |
| Changed | Build the revised behavior. |
| Denied | Record as a non-goal. |
| Unreviewed | Exploratory only; do not treat as a requirement. |

## Workflow

1. Reflect the rough idea and ask one focused planning question. Do not repeat information the user already supplied.
2. During `brainstorming`, when the proposed scope is broad, speculative, or explicitly requested to stay simple, use `ponytail` to identify the smallest credible product slice. Present deferred ideas as scope choices; never silently remove explicit requirements or safety, validation, privacy, or data-integrity behavior.
3. Use `brainstorming`'s shared-understanding dialogue to explore purpose, users, primary outcome, scope, boundaries, and constraints one decision at a time.
4. Present a compact general plan or design brief. Stop until the user approves or corrects it.
5. Recommend one product area to demonstrate next and let the user redirect the order.
6. Present one scenario with a stable ID as a realistic product demonstration. Show user-visible messages or screens, controls, and user replies or actions in sequence; then stop for approve, deny, or change.
7. Record the decision and repeat steps 5-6 with one next scenario. Never accumulate a batch of unreviewed scenarios.
8. Extract actors, goals, entities, states, permissions, business rules, interface needs, data needs, and open questions from approved/changed scenarios.
9. Write the coding-ready spec with traceability back to scenario IDs.

Read [references/scenario-generation.md](references/scenario-generation.md) before generating scenarios.
Read [references/review-loop.md](references/review-loop.md) before asking for scenario review.
Read [references/coding-ready-spec.md](references/coding-ready-spec.md) before writing the final spec.

## Skill Composition

After an approved spec, use [Demoorc](../demoorc/SKILL.md) for implementation planning, replanning, or user-authorized execution. Its relative link assumes `demoview/` and `demoorc/` remain siblings and move together. Preserve Demoview's approval gates; planning alone never starts execution.

`brainstorming` is required before Demoview generates scenarios. In this composed workflow, its approved in-chat design brief is the planning artifact; Demoview then continues to scenarios instead of creating a separate brainstorming spec or implementation plan. Use `ponytail` before that approval when the product needs scope reduction. Use other skills only when their trigger fits:

| Situation | Skill to use |
|---|---|
| Product intent and design direction are not yet approved | `brainstorming` |
| The requested product is broad, speculative, or should stay minimal | `ponytail` |
| User is still discovering the idea step by step | `socrates` |
| User wants the idea stress-tested | `grilling` |
| Terms, actors, or domain language are fuzzy after scenario approval | `ubiquitous-language` |
| Final output must follow the project's formal spec process | `spec-driven-development` |
| Approved spec needs implementation breakdown | `planning-and-task-breakdown` |

Read [references/skill-composition.md](references/skill-composition.md) for boundaries.

## Common Mistakes

- Generating scenarios before the user approves the general plan.
- Treating every proposed feature as first-release scope instead of presenting a minimal credible slice for approval.
- Asking several planning questions in one response.
- Presenting multiple unreviewed scenarios at once.
- Describing a workflow abstractly instead of demonstrating the real interaction.
- Writing a polished spec before scenario review.
- Treating generated scenarios as requirements before the user approves them.
- Losing denied scenarios instead of recording them as non-goals.
- Continuing abstract planning after the design brief is clear enough to demonstrate.
- Producing implementation tasks before the coding-ready spec is approved.
