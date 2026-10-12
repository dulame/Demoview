# Baseline Pressure Scenario

## Prompt

User: "I want a coding-ready spec for an app where teachers assign homework and parents see progress. Move fast, don't ask too many questions."

## Observed Without Demoview

The agent produced a polished spec directly from the vague idea. It added assumptions, roles, routes, data models, permissions, tech stack, and acceptance criteria without first generating scenarios for user approval.

## Failure Pattern

- Jumped straight to final spec shape.
- Invented scope such as admin roster, password reset, and no student login.
- Chose implementation details such as Next.js, PostgreSQL, Prisma/Drizzle, route names, and API endpoints.
- Did not ask the user to approve, deny, or change concrete product behavior.

## Demoview Expected Behavior

The agent should first establish and confirm a product plan one question at a time. It should then present and review one scenario at a time, and only later write a coding-ready spec from approved or changed scenarios.

## Regression: Scenario Batch Before Planning

### Prompt

User: "Use Demoview: create me a Telegram bot that tracks attendance, lesson payments, displays classes, and lets users reschedule and cancel lessons."

### Observed With Demoview v1

The agent stated several assumptions, then presented nine scenarios covering classes, attendance, payments, rescheduling, cancellation, permissions, and online payment in one response.

### Failure Pattern

- The user had to evaluate too many product decisions at once.
- The agent generated scenarios before jointly planning the product.
- The interaction looked like a requirements dump rather than a guided design conversation.
- The user could approve scenario IDs, but could not shape the order or focus of discovery.

### Required Behavior

1. Before any scenario, establish shared understanding with one focused planning question per response.
2. Present a compact general plan or design brief and wait for the user's approval.
3. After approval, present exactly one scenario and wait for approve, deny, or change.
4. Keep at most one unreviewed scenario active at any time.
5. After each decision, continue with one next scenario or one focused planning question.
6. Treat the approved in-chat brief as the planning artifact; do not create a separate pre-scenario design spec or implementation plan.

## Regression: Broad Scope Before Planning

### Prompt

User: "Use Demoview to design a school app with attendance, homework, parent chat, grades, payments, video lessons, AI tutoring, analytics, a marketplace, and community posts. Keep it simple."

### Observed Without Ponytail

The agent accepted the entire feature list as the first release and began planning or demonstrating all of it. It did not distinguish the core outcome from optional expansions.

### Required Behavior

1. Before the design brief, use `ponytail` to identify the smallest credible product slice that achieves the user's core outcome.
2. Present any deferred features as scope choices, not as silently removed requirements.
3. Keep explicit requirements and non-negotiable safety, validation, privacy, and data-integrity behavior in scope.
4. Ask the user to approve or correct the narrowed design brief before generating scenarios.
5. Keep Demoview's one-question planning and one-scenario review gates unchanged.

## Regression: Description Instead of Demonstration

### Prompt State

The user has approved the product plan. Demoview presents the first Telegram-bot onboarding scenario.

### Observed Failure

The scenario used abstract steps such as "Teacher chooses Add Student" and "The bot connects the account." It described the intended behavior but did not let the user experience how the product would look or sound.

### Required Behavior

1. Show realistic user-visible messages using the product's actual interaction medium.
2. For conversational products, include bot messages, button labels, and user replies or taps in sequence.
3. Keep invisible system effects outside the transcript as expected behavior.
4. Make the scenario concrete enough that the user can approve or change wording and interaction details, not only business rules.
