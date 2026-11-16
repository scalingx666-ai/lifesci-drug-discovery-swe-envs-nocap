# Issue

**Title:** #12306 - Refactor: Explicit/implicit Any type clean up from `packages…

## Description

#12306

## How the feature works? / How did you fix the issue?

Removed the `eslint-disable @typescript-eslint/no-explicit-any` and the only `any` (`state: any` in `mapStateToProps`) from `FloatingTools.container.ts`.

`state` is now typed with a local `State` type that describes only the store slices this container reads. It is built from existing types (`FloatingToolsState`, `RequestState`), following the same pattern as other containers (e.g. `Atom.container`, `Bond.container`). The global `StoreState` doesn't include these slices yet.

No runtime behavior changes. This is a type-only change.

Note (not addressed here): the `status` prop in `FloatingTools.tsx` is typed as a single `{ disabled?, hidden? }` object. At runtime it receives a map of action name → status, and the component reads `status[name]` with a cast. `actionState` is typed to match the existing prop contract, so the component file is left untouched.

## Check list
- [ ] unit-tests written — not needed, type-only change; full `ketcher-react` test suite passes (79 suites, 597 tests)
- [ ] e2e-tests written — not needed, no behavior change
- [ ] documentation updated — not needed
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [x] base branch (master or release/xx) is correct
- [ ] task status changed to "Code review"
- [ ] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f13df4841a3d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.