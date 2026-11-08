---
description: Summarize Deixic compliance status for this workspace
---
Read, in this order, with the Deixic MCP tools:

1. `read` with `{"read": "ListControlTests", "params": {"states": ["FRAMEWORK_COVERAGE_STATE_FAILING"]}}` for what is failing now.
2. Ask Dex with `ask_human`: `{"message": "Which programs and frameworks are in scope, and which evidence requests wait on my approval, with their due dates?", "idempotency_key": "<fresh>"}`. If it returns a `resume_token`, pass it back to `ask_human` until the state is `completed`.

Report three short sections: programs (name and framework), failing tests (count on this page, the three oldest, any overdue), and evidence waiting on me (title and due date). Give counts only as the results state them; when a result has `next`, say the list continues. Close with the next action that would most reduce failing tests.
