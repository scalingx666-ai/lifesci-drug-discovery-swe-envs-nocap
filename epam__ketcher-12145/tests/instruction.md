# Issue

**Title:** #12140 – Settings window is out of popup boundaries on large screens

## Description

## How the feature works? / How did you fix the issue?
The Settings dialog had a fixed `height: 70vh`, which is relative to the browser viewport rather than the Ketcher container. In a popup smaller than 70vh of the screen, the dialog overflowed vertically. The only cap (`max-height: 90%`) lived in `.smallScreen`, which applies only to containers ≤600px.

Added `max-height: 90%` to `.settings`. The percentage resolves against `.modalOverlay` (absolutely positioned, `inset: 0`, i.e. the Ketcher container); the dialog body already scrolls, so content stays reachable.

## Check list
- [ ] unit-tests written (CSS-only change; Jest can't assert layout)
- [ ] e2e-tests written
- [ ] documentation updated
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [x] base branch (master or release/xx) is correct
- [ ] task status changed to "Code review"
- [ ] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9ddfc4d140d9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.