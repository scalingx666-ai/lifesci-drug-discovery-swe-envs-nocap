# Issue

**Title:** #12291 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\ui\views\components\StructEditor\InfoPanel.tsx file

## Description

## How the feature works? / How did you fix the issue?

(Screenshots, videos, or GIFs, if applicable)

Removed the file-level `/* eslint-disable @typescript-eslint/no-explicit-any */` from `InfoPanel.tsx`. The only `any` it was hiding was the `connect` state parameter, now typed with the existing `StoreState` (`script/ui/state/store.types.ts`), the same fix as the sibling `InfoTooltip.tsx` (#12292) and the way other `connect` / `mapStateToProps` users do it (`Analyse.tsx`, `Save.tsx`, the `*.container.ts` files).

`store.editor.render.ctab.render` resolves to `Render`, matching the component's `render` prop. The functional-group fields still come from `functionGroupInfoSelector`, so nothing else changes. The `?.` chains and `|| null` fallbacks are kept as-is (the store starts with `editor: null` at runtime).

Type-only change: compiling the branch and master versions of the file gives identical JavaScript.

Verified: ESLint clean on the file (re-adding `store: any` makes `no-explicit-any` report it), Prettier, `tsc`, `npm run test`, `npm run test:types`, `test:circ`. In the browser, hovering a contracted functional group still shows the structure preview panel and hides it on mouse-out.

## Check list

- [ ] unit-tests written
- [ ] e2e-tests written
- [ ] memory bank updated (name the file), or not needed
- [x] PR name follows the pattern `#1234 - issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [ ] base branch (master or release/xx) is correct
- [x] task status changed to "Code review"
- [ ] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `09d9da19c905`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.