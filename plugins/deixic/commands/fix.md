---
description: Fix one failing Deixic test by opening a pull request in your repository
argument-hint: "<test name or id>"
---
Use the `fix-failing-test` skill on the Deixic test "$ARGUMENTS". If "$ARGUMENTS" is empty, run `deixic_list_tests` with `states: ["FRAMEWORK_COVERAGE_STATE_FAILING"]` first and ask which test to fix.
