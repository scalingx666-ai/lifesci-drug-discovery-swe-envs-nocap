# Issue

**Title:** Backmerge: #11889 – Bonds in atomic structures behave as targets for a new connection in macromolecules mode

## Description

## How the feature works? / How did you fix the issue?

Disabled pointer events on atomic bond groups while drawing a connection in Flex and Snake modes. Existing bond hover is cleared when drawing starts, while atom highlighting and targeting remain available.

Normal bond interaction is restored when drawing ends or is cancelled. The selected tool is also cleaned up when the editor is destroyed.

## Validation

- Unit tests: 28 passed across five suites.
- Playwright regression: 2 passed (Flex and Snake).
- Core, macromolecules, and autotest TypeScript checks passed.
- Manual verification in Flex and Snake passed.



## Video

https://github.com/user-attachments/assets/89fbc468-5129-4be5-bdfe-3be84fa0477e



## Check list
- [x] unit-tests written
- [x] e2e-tests written
- [ ] documentation updated
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [x] base branch (master or release/xx) is correct
- [ ] task status changed to "Code review"
- [x] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2dbe707d1831`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.