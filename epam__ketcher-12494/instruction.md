# Issue

**Title:** #12292 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\ui\views\components\StructEditor\InfoTooltip.tsx file

## Description

## How the feature works? / How did you fix the issue?
(Screenshots, videos, or GIFs, if applicable)

Removed the file-level `/* eslint-disable @typescript-eslint/no-explicit-any */` from `InfoTooltip.tsx`. The only `any` it was hiding was the `connect` state parameter, now typed with the existing `StoreState` (`script/ui/state/store.types.ts`), the same way other `connect` / `mapStateToProps` users do (`Analyse.tsx`, `Save.tsx`, the `*.container.ts` files).

`store.editor.render.ctab.render` resolves to `Render`, which matches the component's `render: Render` prop, so no other changes or type assertions were needed. The `?.` chain is kept as-is because the store starts with `editor: null` at runtime.

Type-only change, no behaviour difference.

Verified: ESLint clean on the file (re-adding `store: any` makes `no-explicit-any` report it), Prettier, `tsc`, `npm run test`, `npm run test:types`, `test:circ`. In the browser, hovering a query atom still shows the info tooltip after the delay, positioned inside the canvas, and hides it on mouse-out.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a8bf5c279bd3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.