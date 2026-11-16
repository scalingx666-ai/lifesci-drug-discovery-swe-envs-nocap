# Issue

**Title:** #12294 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-react\src\script\ui\views\modal\modal.types.ts file

## Description

#12294

## How the feature works? / How did you fix the issue?

Removed the `eslint-disable @typescript-eslint/no-explicit-any` and both `any` usages from `modal.types.ts`.

- `BaseProps` and `BaseCallProps` are now generic over the form result type, with safe defaults: `BaseProps<TResult = Record<string, unknown>>`, `BaseCallProps<TResult = unknown>`. Existing dialogs that don't need a concrete shape keep working unchanged.
- Places that actually read fields from the result now declare its shape instead of relying on `any`:
  - `AtomElement.tsx`: new `AtomFormResult` type, used by `Atom.tsx` and `Atom.container.ts`
  - `SGroupFieldset.tsx`: `BaseProps<{ type: string }>`
  - `Open.tsx` / `Open.container.ts`: `OpenResult` type (moved to `Open.tsx` and exported), `onOk: (result: OpenResult) => …`
  - `Automap.tsx` / `Automap.container.ts`: `onOk: (result: AutomapRequest) => …`
- Per review, `Open` and `Automap` declare the result type in the `onOk` callback (container and component props) instead of casting it. The only remaining cast is at the shared `Dialog` boundary (`params={rest as DialogParams}`), the same way `PeriodTable` does it, because `Dialog` still types `onOk` as `(result: unknown) => void`.

No runtime behavior changes. This is a type-only change.

Note (not addressed here): `Dialog` calls `params.onOk(result())` on Enter, and the Open dialog passes `result={() => null}`. If Enter triggers that path, `Open.container`'s `onOk` would read `fragment` from `null`. This comes from reading the code and was not reproduced at runtime. It's worth a separate issue if confirmed.

## Check list
- [ ] unit-tests written — not needed, type-only change; full `ketcher-react` test suite passes (79 suites, 598 tests)
- [ ] e2e-tests written — not needed, no behavior change
- [ ] documentation updated — not needed
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [x] base branch (master or release/xx) is correct
- [ ] task status changed to "Code review"
- [ ] reviewers are notified about the pull request

Memory bank: not needed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `27243f2d33eb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.