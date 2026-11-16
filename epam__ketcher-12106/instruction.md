# Issue

**Title:** #10990 – Refactor: Explicit/implicit Any type clean up from packages/ketcher-core/src/domain/serializers/ket/fromKet/textToStruct.ts file

## Description

## How the feature works? / How did you fix the issue?
Removed all explicit `any` usages (and the file-level `eslint-disable @typescript-eslint/no-explicit-any`) from `packages/ketcher-core/src/domain/serializers/ket/fromKet/textToStruct.ts`.

**Shared KET text types (`ket/types.ts`)**
- Moved the KET text format types (based on the `text` definition in the KET schema) into the shared `ket/types.ts`: `KetTextFont`, `KetTextIndent`, `KetTextStyleOverrides`, `KetTextPart`, `KetTextParagraph`, `KetTextV2Node`.
- Added types for the legacy text node with a `data` wrapper: `KetTextData` and `KetLegacyTextNode`. Added the union `KetTextNode` for both formats.

**`fromKet/textToStruct.ts`**
- `textToStruct(ketItem: KetTextNode, …)`: the internal node is now `TextAttributes`, which `Text` already takes.
- `isKetV2Format` is a proper type guard on `KetTextNode`.
- The Lexical nodes it builds use the existing `SerializedEditorState`, `SerializedParagraphNode` and `SerializedTextNode` types from `retext.ts`. Two small local types add the extra fields written here (`font`, `textFormat`, `textStyle`).
- Legacy `data.content` is typed as `string`, as the KET schema requires. The unreachable branch for Draft.js content passed as an object was removed.

**Duplicate types removed (`toKet/textToKet.ts`)**
- Deleted the private duplicates `KETFont`, `KETIndent`, `KETFontStyleOverrides`, `KETTextPart`, `KETParagraph` and `KETText`, and switched the file to the shared types. `LexicalParagraph` now extends `KetTextStyleOverrides` instead of repeating the style fields.

No runtime behavior changes for valid KET input. Type check, ESLint and Prettier are clean, and the existing serializer unit tests pass (125/125).

## Check list
- [ ] unit-tests written
- [ ] e2e-tests written
- [ ] documentation updated
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [ ] PR is linked with the issue
- [ ] base branch (master or release/xx) is correct
- [x] task status changed to "Code review"
- [ ] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1fd976254e46`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.