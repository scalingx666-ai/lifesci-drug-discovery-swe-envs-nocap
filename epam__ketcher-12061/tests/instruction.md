# Issue

**Title:** #12060 - Refactor: Node.js built-in modules should be imported using the `node:` protocol

## Description

## How the feature works? / How did you fix the issue?

Bare Node.js built-in imports can be ambiguous with third-party packages. All live built-in imports and `require` calls now use the explicit `node:` protocol.

- Updated imports across application code, tests, scripts, and build configs.
- Configured `ketcher-core` Rollup to externalize `node:` imports.

```ts
import { EventEmitter } from 'node:events';
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4fd534e80dc0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.