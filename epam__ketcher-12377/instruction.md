# Issue

**Title:** #12268 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\editor\tool\charge.ts file

## Description

## What
Removed the explicit `any`, the file-level `eslint-disable @typescript-eslint/no-explicit-any` and the implicit `any` parameters from `charge.ts`.

## How
- `charge` is typed as `number`. The tool is only created from the Charge Plus / Charge Minus actions (`opts: 1` / `opts: -1`), and the value is added to the atom's charge.
- The constructor takes `charge: unknown`, as `toolsMap`'s `ToolConstructorInterface` requires, and narrows it with `assert(typeof charge === 'number', …)` from ketcher-core. This avoids adding another `as unknown as ToolConstructorInterface` cast in `tool/index.ts`.
- `mousemove` and `click` take `PointerEvent`, which `editor.hover()` expects, as in the other typed tools.

## Verification
- ESLint is clean, and a planted `any` is reported (the rule is active for this file).
- Prettier, ketcher-react `tsc`, `test:circ`, `npm run test` and `npm run test:types` pass.
- Charge Plus / Charge Minus on an atom: +1, +2, then −1 after three Charge Minus clicks; hover highlight unchanged; no runtime errors.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d29e9d9ba0f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.