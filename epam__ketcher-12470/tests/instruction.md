# Issue

**Title:** #12287 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\ui\state\hotkeys.ts file

## Description

## How the feature works? / How did you fix the issue?
(Screenshots, videos, or GIFs, if applicable)
Removed the file-level `/* eslint-disable @typescript-eslint/no-explicit-any */` from `hotkeys.ts`; it was hiding two `catch (e: any)` clauses in `clipData` and `legacyClipData`.

- The catch variable is now left unannotated, so under the package's `strict` config it is `unknown`.
- The message passed to `editor.errorHandler` (typed `(message: string) => void`) is narrowed with `e instanceof Error ? e.message : String(e)`, the pattern already used in `Editor.ts` and `Editor.tsx`. No type assertions.

Behaviour is unchanged for thrown `Error`s. For a non-`Error` throw, the handler now receives the value as text instead of `undefined`.

Verified: ESLint clean on the file (re-adding `e: any` makes `no-explicit-any` report both lines), Prettier, `tsc`, `npm run test`, `npm run test:types`, `test:circ`. In the browser, copy / cut / paste work, and a forced serialization failure reaches the error handler with the message for both an `Error` and a thrown string.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7bdd70d406b7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.