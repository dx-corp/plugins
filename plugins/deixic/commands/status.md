---
description: Summarize Deixic compliance status for this workspace
---
Read, in this order, with the Deixic MCP tools:

1. `deixic_list_tests` with `states: ["FRAMEWORK_COVERAGE_STATE_FAILING"]` for what is failing now.
2. Ask Dex with `dex_converse_send`: "Which programs and frameworks are in scope, and which evidence requests wait on my approval, with their due dates?" Call `dex_converse_wait` with the returned cursor until the state is `completed`, then read the answer with `dex_converse_read`.

Report three short sections: programs (name and framework), failing tests (count on this page, the three oldest, any overdue), and evidence waiting on me (title and due date). Give counts only as the results state them; when a result has `next`, say the list continues. Close with the next action that would most reduce failing tests.
