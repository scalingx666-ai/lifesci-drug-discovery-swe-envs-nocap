# Issue

**Title:** #12336 - Refactor: react-hooks/exhaustive-deps rule violation clean up from packages\ketcher-macromolecules\src\EditorEvents.tsx file

## Description

ixed the react-hooks/exhaustive-deps violation in EditorEvents.tsx (/packages/ketcher-macromolecules/src/EditorEvents.tsx).

Root cause: The handleMonomersLibraryUpdate callback uses both dispatch and editor, but its useCallback dependency array included only editor. This left out a reactive dependency and could cause the callback to capture an outdated dispatch reference if that dependency changed. A file-wide eslint-disable react-hooks/exhaustive-deps comment was also suppressing the rule for the entire file.

Fix: Added dispatch to the callback's dependency array, changing it to [dispatch, editor]. Removed the file-wide eslint-disable react-hooks/exhaustive-deps comment after checking for additional violations. The existing event subscription and cleanup logic remain unchanged, ensuring that the same callback reference is used for subscription and unsubscription.

Verified: Targeted ESLint passed, including running with --no-inline-config to confirm that the fix does not depend on the suppression comment. The TypeScript check passed, the focused SequenceSyncEditModeButton test passed (4 tests), and git diff --check passed. No unrelated changes were made.

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