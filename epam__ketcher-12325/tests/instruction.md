# Issue

**Title:** #12299 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\ui\views\modal\components\toolbox\Atom\Atom.container.ts file

## Description

## What
Removed the explicit `any` and the file-level `eslint-disable @typescript-eslint/no-explicit-any` from `Atom.container.ts`.

## How
`mapStateToProps` now takes `Pick<StoreState, 'modal'> & { editor: Editor | null }`, built from existing types:
- `StoreState` (`state/store.types.ts`) already describes `modal.form`.
- `Editor` from ketcher-core already declares `isMonomerCreationWizardActive`. It is a type-only import, so there is no new runtime dependency.

The `editor` slice is typed locally rather than added to `StoreState`, to stay within this file and avoid colliding with other open changes to `store.types.ts`. Its default in the store is `null`, so the flag is read with `?.`. The prop was already optional, so behaviour is unchanged.

## Verification
- ESLint is clean, and a planted `any` is reported (the rule is active for this file).
- Prettier, ketcher-react `tsc` and `test:circ` pass; `npm run test` passes.
- The Atom Properties dialog opens and shows the atom's values as before.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `65e93b06f47b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.