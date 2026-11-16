# Issue

**Title:** fix: guard Unix-only resource import so package imports on Windows

## Description

The Unix-only `resource` module does not exist on Windows and the unconditional `import resource` raised `ModuleNotFoundError`, preventing the package (and the test suite) from importing there. The import is now guarded and `report_resource_usage` skips the `getrusage` call when the module is unavailable.

No behavioural change on Linux/macOS. Verified on Windows: package imports and `report_resource_usage` runs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `43094673bf0b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.