# Issue

**Title:** #12285 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\ui\Portal\Portal.tsx file

## Description

## What
Removed the explicit `any`, the file-level `eslint-disable @typescript-eslint/no-explicit-any` and the implicit `any` constructor parameter from `Portal.tsx`.

## How
- `render()` returns `ReactDOM.createPortal(children, this.element)` directly. A `ReactPortal` is already a valid render result, so the `as any` cast (and the temporary variable) were unnecessary.
- `constructor(props)` is typed with the file's existing `Props`.

No casts, no runtime change.

## Verification
- ESLint is clean, and a planted `any` is reported (the rule is active for this file).
- Prettier, ketcher-react `tsc`, `test:circ`, `npm run test` and `npm run test:types` pass.
- Portal users work as before: toolbar dropdowns open and close, the atom context menu opens at the cursor, and abbreviation lookup opens when typing on an empty canvas. No runtime errors.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1a097fcffff9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.