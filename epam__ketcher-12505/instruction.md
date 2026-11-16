# Issue

**Title:** #12316 - Refactor: `no-undef` rule violation clean up from `packages\…

## Description

## How the feature works? / How did you fix the issue?

Removed the file-level `/* eslint-disable no-undef */` from `cliparea.tsx`.

The only `no-undef` violations were the two `as EventListener` casts in `componentDidMount` / `componentWillUnmount`. `EventListener` is a type-only global from TypeScript's DOM lib, so ESLint's `no-undef` does not know it. I replaced it with a local alias derived from the DOM API itself:

```ts
type DomEventListener = Parameters<HTMLElement['addEventListener']>[1];
```

This is exactly the type `addEventListener` / `removeEventListener` accept as the listener argument. Types only, no runtime changes.

Checked: `npm run test` in `ketcher-react` passes (prettier, stylelint, eslint, tsc, dpdm, jest).

## PR type

Tick the row that matches this PR. The full contract is in `.memory-bank/review-workflow.md`.

- [ ] Bug fix: linked issue and a regression test
- [ ] Feature: OpenSpec change in `openspec/changes/<change>/` and tests
- [ ] Large-scale change: opened with `?template=large-scale-change.md`
- [ ] Archive of an OpenSpec change: no unchecked tasks

## Check list

- [ ] unit-tests written
- [ ] e2e-tests written
- [x] memory bank updated (name the file), or not needed
- [x] PR name follows the pattern `#1234 - issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [x] base branch (master or release/xx) is correct
- [x] task status changed to "Code review"
- [ ] reviewers are notified about the pull request

Memory bank: not needed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `43f70e73fb6d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.