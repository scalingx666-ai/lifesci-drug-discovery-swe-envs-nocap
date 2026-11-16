# Issue

**Title:** #11889 – Bonds in atomic structures behave as targets for a new connection in macromolecules mode

## Description

## How the feature works? / How did you fix the issue?
(Screenshots, videos, or GIFs, if applicable)

Backport of #12094 to `release/3.20`. Related issue: #11889.

Disables atomic bond hit targets while drawing a macromolecule connection, using the dedicated `atomic-bond` class on the SVG root and its descendants. Clears existing bond hover when drawing starts and restores interaction when drawing finishes or is cancelled, the tool changes, or the editor is destroyed. Atom targets, polymer bonds, and monomer-to-atom connections remain interactive. The E2E regression locates atomic bonds through data attributes.

Cherry-picked all four source commits in order with `-x`: a77ce3d6ab, 33fb79a891, 1d23296cca, and f78ef9a61b. Resolved the `CoreEditor.destroy()` conflict by adding selected-tool cleanup while retaining the release branch's existing history lifecycle.

## Demo from the original PR #12094:

https://github.com/user-attachments/assets/dcaa40e5-f258-4292-b422-1d39a6ab23f2



Validation:
- Normal pre-push hook passed: all package checks and workspace-wide type checks. Core: 854 tests passed; React: 400 passed; macromolecules: 159 passed. Standalone has no unit tests. Existing skipped tests remain skipped.
- Release-configured Flex/Snake Playwright regression: 2 passed against a fresh Vite source build. Browser logs included a dynamic-import reload error and a Snake renderer assertion despite passing assertions; this is not a claim of error-free browser logs.
- Fresh core build and macromolecules type checks passed. The isolated Escape hotkey case and all three hotkey tests passed on both the backport and exact release base 94b3e70f1f with matching dependencies and fresh core outputs. A temporary probe recorded zero `CoreEditor.destroy()` calls in the isolated Escape test on both branches.
- Formatting, production lint, stylelint, and `git diff --check` passed. An extra forced lint run on normally excluded tests flagged a type-only import in the unchanged source test.


## Check list
- [x] unit-tests written
- [x] e2e-tests written
- [ ] documentation updated
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [x] base branch (master or release/xx) is correct
- [ ] task status changed to "Code review"
- [ ] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `94b3e70f1fbf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.