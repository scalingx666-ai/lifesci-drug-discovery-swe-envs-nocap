# Issue

**Title:** #4545 - The “Open Structure” and the “Save Structure” windows do not block pasting on the canvas

## Description

## How the feature works? / How did you fix the issue?
(Screenshots, videos, or GIFs, if applicable)
## What
In Macromolecules mode, pasting onto the canvas is ignored while a dialog (Open Structure, Save Structure, or any other macro dialog) is open.

## Why
Macro paste is a document-level listener in the core editor, and nothing told it that a dialog was covering the canvas. The open state lives only in the macromolecules Redux slice. Micro mode already ignores clipboard actions while a modal is open (`!state.modal` in `hotkeys.ts`); this brings macro in line.

## How
- `CoreEditor` gets a private `isModalOpen` flag, set through `setIsModalOpen()`, and `pasteEventHandler` returns early while it is set.
- `ModalContainer`, which renders every macro dialog, syncs `selectModalIsOpen` to the editor in an effect.
- The early return doesn't call `preventDefault`, so pasting into fields inside a dialog (e.g. the Open dialog's "Paste from clipboard" textarea) still works.
- A setter is used instead of assigning the property, because `react-hooks/immutability` rejects mutating a value returned from a hook.

## Verification
- Reproduced on master in the browser, then confirmed with the fix: paste is blocked with Open, Save, and Save's File format drop-down open, in Flex, Snake and Sequence (view and text-editing) mode; the dialog's textarea still receives the paste; canvas paste works again after the dialog closes.
- New `ModalContainer.test.tsx` checks the editor is told when a dialog opens and closes; it fails without the fix.
- `npm run test` and `npm run test:types` pass. No rendering change, so no screenshot updates.


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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `460d81145467`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.