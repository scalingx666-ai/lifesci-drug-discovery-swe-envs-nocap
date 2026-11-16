# Issue

**Title:** #12314 - Refactor: no-undef rule violation clean up from packages\ketcher-core\src\utilities\b64toBlob.ts file

## Description

## How the feature works? / How did you fix the issue?
(Screenshots, videos, or GIFs, if applicable)

Removed the file-level `/* eslint-disable no-undef */` from `b64toBlob.ts`. It was hiding one violation: `BlobPart` (a TypeScript DOM-lib type that ESLint's `no-undef` doesn't know) in the cast `new Blob(byteArrays as BlobPart[], …)`.

The cast was added during the TS 6 upgrade (#10062). Since TS 5.7, `Uint8Array` is generic, and the bare `Uint8Array` annotations on `byteArrays` / `byteArray` widened `new Uint8Array(number[])`'s actual type, `Uint8Array<ArrayBuffer>`, to `Uint8Array<ArrayBufferLike>`, which is not a `BlobPart`. Annotating both as `Uint8Array<ArrayBuffer>` keeps the precise type, so `new Blob(byteArrays, …)` type-checks without the cast. No ESLint config change, and one less `as`.

Type-only change: the emitted JavaScript and the function signature are unchanged.

Verified: ESLint clean on the file (re-adding the cast makes `no-undef` report `BlobPart`); `tsc` 0 errors in ketcher-core and ketcher-react; removing the cast while keeping the old annotation fails `tsc`, which proves the annotation is the fix. `npm run test`, `npm run test:types`, `test:circ` pass. Runtime: a base64 → Blob round-trip returns identical bytes for several slice sizes, and in the browser, saving a structure as binary CDX (the only caller) produces a valid `.cdx` that opens back to the same structure.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cc62cb7b1710`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.