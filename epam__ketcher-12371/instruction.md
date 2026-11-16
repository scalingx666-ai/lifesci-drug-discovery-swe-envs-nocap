# Issue

**Title:** #12337 - Refactor: react-hooks/exhaustive-deps rule violation clean up from packages\ketcher-macromolecules\src\components\macromoleculeProperties\MacromoleculePropertiesWindow.tsx file

## Description

Fixed the react-hooks/exhaustive-deps violations in MacromoleculePropertiesWindow.tsx (/packages/ketcher-macromolecules/src/components/macromoleculeProperties/MacromoleculePropertiesWindow.tsx).

Root cause: The chart-rendering effect was missing data.xs and data.ys from its dependency array. These values are derived from the initial chart data using lttb(...). Additionally, the ResizeObserver was created during render and captured containerWidth, resulting in an incomplete dependency list. A file-wide eslint-disable react-hooks/exhaustive-deps comment was suppressing these violations.

Fix: Memoized the LTTB chart data using useMemo with initialData as its dependency and added data.xs and data.ys to the chart-rendering effect's dependency array. Moved ResizeObserver creation inside its useEffect and used a functional state update to avoid capturing containerWidth. The observer is disconnected and the debounced callback is cancelled during cleanup. Removed the file-wide ESLint suppression.

The chart continues to clear and redraw its SVG when the chart data or container width changes. No unrelated files were modified.

Verified: Both targeted ESLint checks passed, including running with --no-inline-config to confirm the fix does not depend on the suppression comment. The macromolecules TypeScript check and unit test suite passed, and git diff --check passed. No dedicated component tests were added for this refactor.

## Check list
- [ ] unit-tests written
- [ ] e2e-tests written
- [ ] documentation updated
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [x] base branch (master or release/xx) is correct
- [x] task status changed to "Code review"
- [x] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d29e9d9ba0f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.