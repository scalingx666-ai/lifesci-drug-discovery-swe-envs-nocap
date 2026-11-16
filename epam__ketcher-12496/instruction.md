# Issue

**Title:** #12289 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\ui\state\functionalGroups\index.ts file

## Description

## How the feature works? / How did you fix the issue?
(Screenshots, videos, or GIFs, if applicable)
Removed the file-level `/* eslint-disable @typescript-eslint/no-explicit-any */` from `functionalGroups/index.ts`. It was hiding 3 `any`s, all describing the same value: the functional-group hover info stored by `FG_HIGHLIGHT` (`FGState.functionalGroupInfo`, and the `group` parameter of `highlightFGroup` / `notDebouncedHighlightFG`).

They are now typed with a `FunctionalGroupInfo` union that lists exactly what callers dispatch through `highlightFG`:
- `InfoPanelData` (existing type from `functionalGroupsTooltip.ts`): hover data `{ groupStruct, event, sGroup }` from `onShowInfo`
- `{ groupStruct: null; sGroup: null }`: hover end, from `onShowInfo`
- `{ group: null; id: null }`: clear after Expand/Remove, from the functional-group context-menu hooks

The state field is `FunctionalGroupInfo | null` (initial state). Because `memoizedDebounce` infers its arguments from the wrapped function, all four call sites are now type-checked. No type assertions, no runtime change.

Note: the two "clear" shapes differ for historical reasons. Unifying them (e.g. dispatching `null`) would touch three other files, so it is left for a possible follow-up.

Verified: ESLint clean on the file (re-adding `group: any` makes `no-explicit-any` report it), Prettier, `tsc`. Narrowing the type to `InfoPanelData` alone makes `tsc` reject exactly the three "clear" call sites, confirming the union matches real usage. `npm run test`, `npm run test:types`, `test:circ` pass. In the browser, hovering a contracted functional group (CF3) shows the info panel, moving away hides it, and Expand Abbreviation from the context menu leaves it hidden.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `43f70e73fb6d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.