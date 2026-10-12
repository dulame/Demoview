# Routing Cases

These cases describe expected decisions; they are examples, not a claim that automated tests have passed.

| Case | Request/context | Expected route and boundary |
|---|---|---|
| 1 | Fix a typo in an approved spec | Luna medium; no delegation needed. |
| 2 | Inventory existing screens for an approved feature | Luna medium; report evidence and gaps. |
| 3 | Implement a routine isolated settings form after user requests execution | Terra high; keep edits within assigned files and verify acceptance criteria. |
| 4 | Design a change to authentication and permissions | Astra high leads design/review; implementation may remain Terra high. Require an execution request before delegation. |
| 5 | Plan a production data migration | Astra high for architecture and critical verification; never run migration automatically. |
| 6 | User requests only a task plan | Route tasks by risk, present ownership/dependencies, and stop without starting agents or code. |
| 7 | Add ordinary unit tests for a routine feature | Terra high; treat as routine verification unless results or scope expose elevated risk. |
| 8 | Test replay behavior for money movement | Astra high leads test design/review and critical verification; implementation may remain Terra high. |
| 9 | User requests an unavailable model | Explain it is unavailable and ask before substituting another model. |
| 10 | An implementation uncovers an authentication risk | Escalate automatically to Astra high within the approved routes, explain briefly, checkpoint, and stop/wait/cancel the current owner before reassigning overlapping files. |
| 11 | Existing balance-integrity requirement needs replay regression tests | Treat as maintenance derived from the existing requirement; add the necessary checks without a new product-scenario gate. Seek Demoview approval only if proposing new user-visible policy or behavior. |
