# Issue

**Title:** #12296 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\ui\views\modal\components\meta\Settings\Settings.tsx file

## Description

## How the feature works? / How did you fix the issue?
(Screenshots, videos, or GIFs, if applicable)
Removed the file-level `/* eslint-disable @typescript-eslint/no-explicit-any */` from `Settings.tsx` and typed the two `any` props using types that already exist:

- `initState: any` → `SettingsFormValue` (from `ketcher-core`). The prop is filled from `state.options.settings`, which `OptionsState` already declares as `SettingsFormValue`.
- `onOpenFile: (any) => void` → `(content: File | FileContent) => void`. The parameter was literally named `any`, so it was implicitly `any`. The new signature is exactly what `OpenButton` passes to `onLoad` (it hands over a raw `File` when no file reader is available).

Type-only change, no runtime difference: compiling the branch and master versions of the file gives the same JavaScript.

Verified: ESLint clean on the file (re-adding `initState: any` makes `no-explicit-any` report it), Prettier, `tsc`, `npm run test`, `npm run test:types`, `test:circ`. In the browser, the Settings dialog still works: Reset enables after a change, Open from file loads settings (an invalid file is ignored), Apply saves.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8e57a7f3bca0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.