# Issue

**Title:** #12280 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\ui\data\convert\structConverter.ts file

## Description

## What
Removed the explicit `any` and the file-level `eslint-disable @typescript-eslint/no-explicit-any` from `structConverter.ts`.

## How
Both `any`s were element types of arrays built from the struct, whose types already exist in ketcher-core:
- `Array.from(struct.atoms.values())` is `Array<Atom>`, matching the SMARTS branch in the same function.
- `Array.from(struct.rxnArrows.values())` is `Array<RxnArrow>` (`mode: RxnArrowMode`).

No casts, no runtime change.

## Verification
- ESLint is clean, and a planted `any` is reported (the rule is active for this file).
- Prettier, ketcher-react `tsc`, `test:circ`, `npm run test` (including `structConverter.test.ts`) and `npm run test:types` pass.
- Save dialog warnings are unchanged: a generic atom (`C*`) saved as SMILES warns about generic atoms, and a filled-triangle reaction arrow saved as Rxnfile V2000 warns that it will be replaced. Neither warning appears for plain structures or the default arrow.

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