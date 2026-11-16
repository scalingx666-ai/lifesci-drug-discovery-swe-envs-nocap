# Issue

**Title:** #4170 - Macro: lack of tooltips for the Fullscreen and the Select Rectangle buttons in the hover state

## Description

<img width="959" height="491" alt="1" src="https://github.com/user-attachments/assets/f6e78188-341e-4d2a-b86b-4acc5c9ffd19" />

## What
The Fullscreen button in Macromolecules mode now shows the "Fullscreen mode" tooltip on hover, the same as in Molecules mode (Chinese: 全屏模式).

## Why
The macromolecules `FullscreenButton` rendered its `IconButton` without a `title`, so there was no tooltip. The Select Rectangle button already has its tooltip in Macromolecules mode ("Select Rectangle (Shift+Tab)"); the issue was reopened only for Fullscreen.

## How
`FullscreenButton` takes its title from the macromolecules namespace (`buttons.fullscreen`), as the Help and About buttons beside it do. The new key is added to `en` and `zh-CN`, using the same wording as Molecules mode; the locale completeness check (#12081) requires both.

## Verification
- Browser: the Macromolecules Fullscreen button shows "Fullscreen mode" (also while in fullscreen), and 全屏模式 with the Chinese UI, matching Molecules mode.
- New case in `FullscreenButton.test.tsx`; fails on master (no title).
- Removing the zh-CN key makes `tsc` fail, confirming the locale completeness check covers it.
- `npm run test` and `npm run test:types` pass. No screenshot changes (a native tooltip isn't captured in screenshots).


## Check list
- [ ] unit-tests written
- [ ] e2e-tests written
- [ ] documentation updated
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [ ] base branch (master or release/xx) is correct
- [x] task status changed to "Code review"
- [ ] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1fd976254e46`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.