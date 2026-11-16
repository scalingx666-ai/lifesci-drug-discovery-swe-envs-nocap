# Issue

**Title:** #12338 - Refactor: react-hooks/exhaustive-deps rule violation clean up from packages\ketcher-react\src\script\ui\App\App.tsx file

## Description

Fixed the react-hooks/exhaustive-deps violation in App.tsx (/packages/ketcher-react/src/script/ui/App/App.tsx).

Root cause: The application initialization effect used checkServer, dispatch, and ketcherId, but its dependency array was empty. A file-wide eslint-disable react-hooks/exhaustive-deps comment was suppressing the violation.

Fix: Added [checkServer, dispatch, ketcherId] to the effect's dependency array and removed the file-wide ESLint suppression. The server check, template initialization, cleanup actions, and Ketcher instance removal remain in the same effect. The dependency values are stable under the current application wiring, preserving the intended initialization and cleanup behavior.

Added a focused test in App.test.tsx to verify that initialization does not repeat when the component rerenders with unchanged dependencies and that the correct Ketcher instance is removed on unmount.

Verified: ESLint with --no-inline-config passed, the focused App.test.tsx test passed (3 tests), the package TypeScript check passed, and git diff --check passed. The initial Jest attempt encountered a sandbox permission error, but the in-band retry outside the sandbox passed. No unrelated files were modified.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cddfcb9cf9e8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.