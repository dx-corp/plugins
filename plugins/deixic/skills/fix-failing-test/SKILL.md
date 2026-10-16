---
name: fix-failing-test
description: Use when the person asks to fix a failing Deixic test, for example a GitHub branch-protection, GCP IAM or logging, or Google Workspace setting test. Reads the failing resources from Deixic, changes the customer's repository or infrastructure code, and opens a pull request.
---

# Fix a failing Deixic test with a pull request

The fix lands in the person's own repository. Deixic re-runs the test after the change is live; this skill does not mark anything passed.

## 1. Read the failure
- Find the test: `deixic_list_failing_tests` with `search` set to the name, or use the id given.
- `deixic_get_test` with `check_object_id`: list every failing resource and the evidence that shows the failure (the setting read, its value, the expected value).
- `deixic_get_test_remediation`: note the deadline and any earlier fix.

## 2. Find where the setting is managed
Search the current repository before writing anything:
- **GitHub** (branch protection, required reviews, secret scanning, Dependabot, CODEOWNERS): look for Terraform `github_*` resources, `.github/settings.yml`, or repository rulesets as code. If no config manages the setting, the fix is a settings change, not a PR: give the exact path in GitHub settings and stop.
- **GCP** (IAM bindings, public buckets, audit logging, key rotation, VPC flow logs): look for Terraform `google_*` resources or Config Connector YAML. Change the resource that owns the failing project, bucket or binding; do not add a second resource for the same object.
- **Google Workspace** (2-step verification, password policy, sharing, admin roles): usually not code. If the repository uses the `googleworkspace` Terraform provider, change it there; otherwise give the Admin console path and stop.

## 3. Change and verify
- Make the smallest change that makes each failing resource match the expected value in the evidence. Touch nothing else.
- Run the repository's own checks (`terraform fmt` and `terraform validate`, linters, tests). If `terraform plan` is available, show the planned change for the failing resources only.

## 4. Open the pull request
- Branch `deixic/fix-<short-test-name>`; commit message and PR title name the test.
- PR body: the Deixic test name and id, the failing resources, the evidence before the change, the change made, how it was verified, and that Deixic re-checks the test after deploy.
- Use `gh pr create`. Do not merge.

## 5. Report
Give the PR link, the resources it fixes, and any failing resource it does not fix and why. If the person wants an owner assigned in Deixic, say which tool would do it once write access is granted.
