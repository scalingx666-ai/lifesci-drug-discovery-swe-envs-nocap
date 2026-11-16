# Issue

**Title:** #12313 - Refactor: `no-undef` rule violation clean up from `packages\…

## Description

#12313

## How the feature works? / How did you fix the issue?

Removed the `eslint-disable no-undef` from `hoverPath.ts`.

The violations came from type annotations that referenced the global `paper` namespace (`paper.Path`, `paper.CompoundPath`, `paper.PathItem`). paper.js declares its types as an ambient global namespace, which TypeScript resolves but ESLint's `no-undef` does not know about.

- Added local type aliases based on the already imported `paperjs` module: `PaperPath`, `PaperCompoundPath`, `PaperPathItem` = `InstanceType<typeof paperjs.X>`. The same approach is already used in `ReplacementHighlightView.ts`.
- `paperjs.Path` can't be used as a type directly, because the `paper` module exports a `PaperScope` instance, not a namespace.
- Declaring `paper` as an ESLint global was not done: it would affect the whole repo and could hide real runtime references to an undeclared `paper`.

The resolved types are identical. No runtime behavior changes.

## Check list
- [ ] unit-tests written — not needed, type-only change; full `ketcher-core` test suite passes (119 suites, 1169 tests)
- [ ] e2e-tests written — not needed, no behavior change
- [ ] documentation updated — not needed
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [x] base branch (master or release/xx) is correct
- [ ] task status changed to "Code review"
- [ ] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `43f70e73fb6d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.