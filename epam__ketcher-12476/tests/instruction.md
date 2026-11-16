# Issue

**Title:** #12309 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\ui\views\toolbars\RightToolbar\AtomsList\AtomsList.tsx file

## Description

#12309

## How the feature works? / How did you fix the issue?

Removed the `eslint-disable @typescript-eslint/no-explicit-any` and the `props: any` annotation in `StyledAtom` from `AtomsList.tsx`.

- `styled(Atom)` already infers its props from the `Atom` component (`el: Element`, `shortcut`, `selected`, button attributes), so the annotation is simply dropped. No new types or imports are needed.
- Without `any`, TypeScript shows that `Elements.get(label)` can return `undefined`, while `Atom` requires `el`. Added `if (!element) return null;` instead of a non-null assertion or a cast.

Behavior: labels come from the hardcoded `basicAtoms` list, and all of them exist in `Elements`, so nothing changes in practice. For an unknown label, `Atom` would previously throw on `el.title`. Now that button is skipped.

Note: the open PR #12344 also edits this file (imports and the `status` type). I checked with a test merge: the two changes merge cleanly.

## Check list
- [ ] unit-tests written — not needed; full `ketcher-react` test suite passes (79 suites, 597 tests)
- [ ] e2e-tests written — not needed, no behavior change for existing atoms
- [ ] documentation updated — not needed
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [x] base branch (master or release/xx) is correct
- [ ] task status changed to "Code review"
- [ ] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `43f70e73fb6d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.