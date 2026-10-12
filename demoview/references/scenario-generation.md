# Scenario Generation

## Purpose

Generate one concrete example the user can react to. A scenario is not a requirement until reviewed.

## Coverage Areas

Use these areas to choose the next scenario. They are a private coverage checklist, not a batch to present all at once.

| Area | What to show |
|---|---|
| Primary happy path | The most successful end-to-end user outcome. |
| Alternate path | A valid but different way the user may reach the goal. |
| Invalid input | Bad, missing, late, contradictory, or unsupported input. |
| Permission boundary | Who can and cannot do the behavior. |
| Empty state | First-time use, no data, no matches, or no setup. |
| Failure state | External service failure, save failure, timeout, or unavailable data. |
| Admin/internal flow | Back-office, moderation, configuration, or owner workflow. |
| Lifecycle edge | Edit, cancel, delete, archive, retry, restore, expire, or handoff. |

## Format

Use stable IDs so the final spec can trace requirements back to reviewed scenarios. The Demo is a concrete simulation of the product, not a summary of what happens.

Match the demonstration to the product's interaction medium:

| Product | Demonstration |
|---|---|
| Chatbot or conversational UI | Realistic messages, button labels, user replies, and taps in order. |
| Screen-based app | Screen states, visible copy, controls used, and resulting state. |
| CLI | Commands and representative output. |
| API | Requests, responses, and observable state changes. |
| Service or workflow | Concrete actor dialogue, decisions, and visible outcomes. |

Keep internal processing out of the transcript. State invisible effects separately under Expected behavior.

````md
### S01: Student joins a class through a bot

**Status:** Unreviewed
**Actors:** Teacher, Student
**Preconditions:** The teacher has created the student record.

**Demo:**

Teacher's chat:

```text
Bot: The student profile is ready.
[Send invite] [Copy link]

Teacher taps: Send invite
```

Student's chat:

```text
Bot: Your teacher invited you to join the class.
[Join class]

Student taps: Join class

Bot: You joined successfully.
```

**Expected behavior:** The student account becomes connected to the teacher's class.
**Questions exposed:** Does the invitation expire?
````

## Generation Rules

- Present exactly one new scenario per response.
- Keep at most one scenario in Unreviewed status.
- Ask for approve, deny, or change immediately after that scenario.
- After the user decides, record the status before selecting the next product area.
- Let the user redirect which area is demonstrated next.
- Use product language the user used, but flag unclear terms.
- Use exact proposed copy and controls when wording or interaction matters.
- Prefer observable behavior over implementation guesses.
- Explore questionable or likely non-goal behavior only as its own candidate scenario.
- Avoid choosing tech stack, database, routes, or components unless the rough spec already gives them.
- Do not preview several unwritten scenarios. A short coverage summary may name reviewed areas and recommend one next area.
