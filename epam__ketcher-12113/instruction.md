# Issue

**Title:** #7227 - Unexpected on-screen keyboard activation on tablet

## Description

Fix: Unexpected on-screen keyboard activation on tablet (#7227)                                                                                                                                                                                                 
   
Problem                                                                                                                                                                                                                                                                         
On touch devices (tablets), opening the zoom input field triggered the system's virtual keyboard to appear. This happened because:

1. ZoomInput (both in ketcher-react and ketcher-macromolecules) unconditionally called focus() and select() on mount — which on touch devices signals the browser to open the on-screen keyboard.
2. ClipArea — the hidden contentEditable div used for clipboard operations — had autoFocus set, causing the virtual keyboard to open immediately on page load on touch devices.

Changes
ZoomInput.tsx (both packages)
- Auto-focus on mount is now skipped on touch devices (detected via 'ontouchstart' in window || navigator.maxTouchPoints > 0).
- Added inputMode="numeric" so that when a touch user does tap the field manually, the keyboard shows a numeric layout instead of a full keyboard.

cliparea.tsx
- Added readOnly and inputMode="none" to the hidden clipboard textarea. This prevents the virtual keyboard from activating when the ClipArea element receives focus, while preserving its clipboard functionality.

Why
On tablets, unexpected virtual keyboard pop-ups cover a significant portion of the screen and disrupt the editing workflow. These changes ensure the keyboard only appears when the user explicitly taps an editable field, not as a side effect of component mounting or clipboard initialization.


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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0cc894b4c7ae`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.