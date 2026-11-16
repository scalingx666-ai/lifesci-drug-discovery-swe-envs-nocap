# Issue

**Title:** #12288 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\ui\state\shared.ts file

## Description

## How the feature works? / How did you fix the issue?
(Screenshots, videos, or GIFs, if applicable)
Removed the file-level `/* eslint-disable @typescript-eslint/no-explicit-any */` from `shared.ts`. It was hiding one `any`: the `catch (error: any)` in `load()`.

- The catch variable is now unannotated, so under the package's `strict` config it is `unknown`.
- The message passed to `editor.errorHandler` (typed `(message: string) => void`) is narrowed with `error instanceof Error ? error.message : String(error)`, the pattern already used in `Editor.ts` and `Editor.tsx`. No type assertions. The existing `if (error)` guard is kept.

Behaviour is unchanged for thrown `Error`s, which is everything `load` can catch today (Indigo, the formatters and the editor all throw `Error`). A non-`Error` throw now reaches the handler as text instead of `undefined`.

Verified: ESLint clean on the file (re-adding `error: any` makes `no-explicit-any` report it), Prettier, `tsc`, `npm run test`, `npm run test:types`, `test:circ`. In the browser, Open → Paste loads a valid structure, and invalid text still reports Indigo's "Convert error! …" message through the error handler.

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