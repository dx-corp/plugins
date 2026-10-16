---
description: List the Deixic tests that are failing now
argument-hint: "[framework, provider or search text]"
---
Call the Deixic MCP tool `deixic_list_failing_tests`. If "$ARGUMENTS" is not empty, narrow the call: a provider name (github, gcp, google_workspace, aws, okta) goes in `source_providers`; anything else goes in `search`.

Show one row per test: test name, control, framework, owner (or "no owner"), SLA state, and how long it has failed. Sort by SLA state, overdue first. If the result has `next`, say the list continues and offer to read the next page. Do not state a total the result does not give.

End with the single test you would fix first and why, then `/deixic:fix <that test>`.
