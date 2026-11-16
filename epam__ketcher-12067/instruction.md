# Issue

**Title:** #12066 - Refactor: `structuredClone()` should be used instead of other deep cloning methods

## Description

## How the feature works? / How did you fix the issue?
Replace JSON stringify/parse deep clones with the standardized structured clone API in settings persistence, service snapshots, and the integration-test fixture. Expose Node’s native API in Jest’s jsdom setup.

```ts
this.storage.set(key, globalThis.structuredClone(settings));
```

## Check list
- [ ] unit-tests written
- [ ] e2e-tests written
- [ ] documentation updated
- [ ] PR name follows the pattern `#1234 – issue name`
- [ ] branch name doesn't contain '#'
- [ ] PR is linked with the issue
- [ ] base branch (master or release/xx) is correct
- [ ] task status changed to "Code review"
- [ ] reviewers are notified about the pull request

<!-- START COPILOT CODING AGENT SUFFIX -->

-

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b0019f70e47`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.