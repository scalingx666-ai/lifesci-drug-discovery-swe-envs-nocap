# Issue

**Title:** #12326 - Refactor: object-shorthand rule violation clean up from packages\ketcher-core\src\domain\entities\atom.ts file

## Description

## What
Removed the file-level `eslint-disable object-shorthand` from `atom.ts` and fixed the two violations it hid.

## How
The `pseudo` accessor defined in the `Atom` constructor via `Object.defineProperty` now uses method shorthand: `get() {…}` and `set(value) {…}` instead of `get: function () {…}` and `set: function (value) {…}`. Method shorthand keeps the same dynamic `this`, so the behaviour is unchanged.

## Verification
- ESLint is clean, and a planted `get: function ()` is reported (the rule is active for this file).
- Prettier, ketcher-core `tsc`, `atom.test.ts`, `npm run test` and `npm run test:types` pass.
- Pseudo atoms (`Pol`, `Q`) load, render in italics and save back unchanged, and setting a pseudo label through Atom Properties (Atom Type: Special) applies.

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