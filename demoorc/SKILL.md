---
name: demoorc
description: Orchestrate user-authorized implementation and planning for approved Demoview specs with risk-based task ownership and model routing.
---

# Demoorc

Demoorc coordinates planning, implementation, and replanning from an approved Demoview spec. Invoke it when the user requests planning or execution, not automatically when a spec is completed. Plan-only requests stop at the plan; implementation and delegation require user authorization.

Keep `demoview/` and `demoorc/` as sibling directories in the same package: their relative links depend on that layout, so move them together. This package is not a global skill installation.

## Approval Boundary

- Read [Demoview](../demoview/SKILL.md) and its [composition rules](../demoview/references/skill-composition.md) when working from a Demoview spec.
- For new product behavior, plan only from the approved brief/spec and approved or changed scenarios. Denied scenarios remain non-goals; unreviewed scenarios are not requirements. Requested maintenance and bug fixes may trace to the explicit user request or an existing requirement without creating a new product scenario.
- Necessary engineering safeguards and regression tests may derive from approved behavior, including auth isolation and duplicate-payment/replay checks; they do not need separate product-scenario approval. If work discovers a genuinely new user-visible policy or behavior, return to Demoview and request approval for one scenario before implementing that behavior.
- Preserve Demoview's brainstorming approval and one-scenario-at-a-time approval loop. Never advance it on Demoview's behalf.
- Before any implementation or agent delegation, confirm the user has requested that execution. If only planning was requested, return the plan and stop.

## Routing

Choose routing by task complexity and blast radius. These are preferred model and effort assignments, subject to controls available in the current runtime:

| Work | Preferred route |
|---|---|
| Small documentation, inventory, or low-risk isolated task | `gpt-6-luna`, medium |
| Routine coding and testing; ordinary feature implementation | `gpt-5.6-terra`, high |
| Difficult architecture, high-blast-radius change, or critical verification | `gpt-6-astra`, high |

Auth, money movement, data migrations, and other critical paths require Astra-led design/review and testing. Routine code may remain with Terra under Astra's design or review. A simple isolated code change may use Luna only when both risk and blast radius are low. Tiny tasks do not need a three-agent team.

Inspect available subagent and model-routing capabilities in the current runtime before assigning work. Astra coordinates when available; do not claim to switch the parent model. Do not invent parallel roles or describe unlaunched agents as active. For user-authorized execution, automatically reclassify, escalate, or reassign unfinished work within these three approved routes when new risk or complexity warrants it; briefly explain the change, with no new confirmation. Ask before substituting an unavailable requested model or changing an explicit budget or scope limit.

Use the available subagent tools for authorized delegation; do not create user-visible chats. Split work only when dependencies and file ownership allow genuinely independent progress. Assign disjoint write ownership, keep shared interfaces with one owner, and avoid duplicate investigation or blockers.

## Work Tracking

For each task, track:

- Task ID and approved scenario/spec reference or explicit maintenance request; for derived safeguards, record the approved behavior that motivates them.
- Dependencies, risk/blast radius, and acceptance criteria.
- Owned files, assigned model and effort, and status.

On replan, update only affected tasks and dependencies. Before handing the same files to a new owner, checkpoint existing edits and stop/cancel or wait for the current task to finish; then hand off only unfinished parts. Record the reason and new owner/route.

Before reporting completion, verify acceptance criteria with suitable checks and report what was and was not verified. Do not automatically deploy, delete data, or run migrations. Such actions require explicit user authorization and appropriate safeguards.

## Example

For an approved profile-settings spec, plan the UI and API tasks with Terra high, identify their file ownership and dependency, and reserve an Astra high review if the work changes authentication or access control. If the user asked only for a plan, stop after presenting it. Delegate implementation only after the user requests execution and runtime capabilities have been checked.

See [routing cases](tests/routing-cases.md) for compact examples used to sanity-check routing decisions.
