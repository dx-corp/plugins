---
name: answer-evidence-request
description: Use when the person needs to answer an auditor's evidence request or asks what evidence exists for a control in Deixic. Finds the request, the controls and tests behind it, and the current evidence, and drafts the response.
---

# Answer an auditor evidence request

1. Find the request: `deixic_list_evidence` with `search` set to the request title or control, or `audit_id` for one audit's requests. Note owner, due date, status, linked controls and frameworks.
2. For each linked control, call `deixic_get_control` (`control_id`) to see its tests and current state.
3. For each automated test on those controls, call `deixic_get_test` and `deixic_list_test_runs` to get the latest result, when it ran, the source it read, and the per-resource evidence.
4. Draft the response:
   - what the control requires, in one sentence;
   - the evidence that meets it: each item with its source system, the date it was collected, and the test run it came from;
   - any gap: a failing resource, a stale run, or a missing document. State the gap; do not paper over it.
5. Show the draft to the person. Do not submit, attach or change anything in Deixic from this skill.

Use only dates and results the tools return. If a read is refused or a list has `next` you did not read, say so in the draft.
