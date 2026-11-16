# Issue

**Title:** Allow value rendering using renderers processor from API

## Description

Use it like this:
```kotlin
renderWithHost<C> { host, value: C -> notebook.renderersProcessor.renderValue(host, value_to_be_rendered) }
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8e3677d777c3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.