# Issue

**Title:** #12058 - Refactor: Node.js built-in modules should be imported using the `node:` protocol

## Description

## How the feature works? / How did you fix the issue?
Node.js built-ins used bare module names, which could be confused with npm packages. Updated the issue-reported imports and requires to use explicit `node:` specifiers.

- **ES modules:** Prefixed built-in imports in the Vite/Rollup configs and file transformers.
- **CommonJS:** Prefixed `fs` and `path` requires in the schema compilation script.

```js
import path from 'node:path';
const fs = require('node:fs');
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