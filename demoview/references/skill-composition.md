# Skill Composition

## Principle

Demoview owns the scenario-to-spec contract. `brainstorming` owns the required planning conversation before scenarios. `ponytail` reduces unnecessary scope before the design brief is approved. Other skills can improve specific phases, but they should not bypass planning or scenario review.

## Composition Rules

| Skill | Use when | Boundary |
|---|---|---|
| `brainstorming` | Every new Demoview design, before generating scenarios. | Use its shared-understanding dialogue and approval pattern. The approved in-chat brief is its artifact in this composed workflow; then return to Demoview instead of writing a separate design document or implementation plan. |
| `ponytail` | The proposed product is broad, speculative, or the user asks for a simple or minimal solution. | Before the design brief, recommend the smallest credible slice and show deferred ideas as scope choices. Do not remove explicit requirements or weaken safety, validation, privacy, or data-integrity behavior. |
| `socrates` | The user has no clear starting idea and wants guided discovery. | Return to Demoview's brainstorming phase once there is enough raw intent to plan the product. |
| `grilling` | The user wants the concept stress-tested or asks to be grilled. | Grill assumptions before final spec, not after implementation starts. |
| `ubiquitous-language` | Approved scenarios reveal confusing, overloaded, or competing terms. | Use the glossary to improve the spec; do not let glossary guesses create requirements. |
| `spec-driven-development` | The repository or user requires a formal spec workflow. | Demoview scenarios provide evidence for the spec. Preserve approval gates. |
| `planning-and-task-breakdown` | The Demoview spec is approved and the user wants implementation tasks. | Do not plan from unapproved scenarios. |
| `demoorc` | The user requests implementation planning, replanning, or execution for an approved spec. | Coordinate task ownership and routing; execute only when the user authorized execution. Preserve all Demoview approval gates. |

## Anti-Pattern

Do not generate scenarios before the brainstorming brief is approved. Do not invoke implementation planning to "save time" before scenario review. Either shortcut recreates the failure Demoview exists to prevent: plausible specs built from unconfirmed assumptions.

Do not use `ponytail` to silently discard requested behavior. The user approves the proposed minimum scope in the design brief before Demoview starts scenario review.

Demoorc is available only after the relevant design brief and scenarios are approved. Its task plan is not permission to start implementation; the user must request implementation or delegation. Its link assumes `demoview/` and `demoorc/` remain siblings and move together; this is a package-local skill, not a global installation.
