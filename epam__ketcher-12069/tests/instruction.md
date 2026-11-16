# Issue

**Title:** #12029 – Refactor: Let's rewrite `packages/ketcher-react/src/script/ui/views/modal/components/InfoModal/InfoModal.test.utils.js` from JavaScript to TypeScript

## Description

## How the feature works? / How did you fix the issue?
(Screenshots, videos, or GIFs, if applicable)

Refactiored `InfoModal.test.utils.js` to TypeScript (`InfoModal.test.utils.tsx`) and removed all implicit `any` types.

- Typed `renderWithMockStore` parameters: `component: ReactElement`, `initialState: InfoModalMockState`, `store: Store<InfoModalMockState>`.
- Added a local `InfoModalMockState` interface for the mock store shape (`options.app.errorMessage`). It's test-only, so it isn't added to the shared types.
- Replaced `createStore(modalReducer, initialState)` with `legacy_createStore` and a pass-through reducer. The mock state isn't a `ModalState`, so using `modalReducer` would need an unsafe cast. At runtime it only returned the state unchanged, so behavior is the same. 
(`legacy_createStore` avoids the Redux 5 deprecation warning without adding `@reduxjs/toolkit`.)
- No changes to `InfoModal.test.tsx`; the import path resolves to the new file.


## Check list
- [ ] unit-tests written
- [ ] e2e-tests written
- [ ] documentation updated
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [ ] PR is linked with the issue
- [ ] base branch (master or release/xx) is correct
- [x] task status changed to "Code review"
- [ ] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b0019f70e47`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.