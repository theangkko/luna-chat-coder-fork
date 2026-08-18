---
name: ci-forensics
description: Diagnose GitHub Actions failures by correlating the exact run, job, commit SHA, source state, and failing log before changing code or retrying.
license: MIT
metadata:
  version: "0.1.0"
---

# CI Forensics

Use this skill when a GitHub Actions workflow fails, is unexpectedly green, or appears inconsistent with the source the agent believes it executed.

## Required investigation order

```text
workflow run
  -> job
  -> exact commit SHA
  -> exact checked-out source
  -> failing step/log
  -> root-cause classification
```

Do not infer the cause from a red conclusion alone. Verify the failing job and the source identity first.

## Root-cause classes

Classify the failure as one or more of:

- workflow/runtime infrastructure
- dependency or SDK
- compile/build
- test harness or fixture
- product logic
- packaging/publish
- repository permissions or policy

## Test discipline

Never change an assertion only because the observed value is different. Determine the intended semantic behavior first. Integration fixture failures can expose a real product defect.

## Retry discipline

Diagnose before retrying. Re-run a failed job only when the source is unchanged or when the retry itself is the intended verification. After a source change, verify the new commit rather than relying on an old run.

## Completion evidence

A task is not CI-complete until the relevant build/test/publish checks actually passed against the exact commit being reported as complete.
