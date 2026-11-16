# Issue

**Title:** #12384 - Refactor: unicorn/better-dom-traversing rule violation clean up

## Description

## How the feature works? / How did you fix the issue?
Four indexed first-child accesses in atom and bond rendering violate `unicorn/better-dom-traversing`.

- **Traversal:** Replace `childNodes[0]` with `firstChild`, preserving node selection.
- **Regression coverage:** Verify stereo color, opacity, and escaped query tooltips target only the first SVG `<tspan>`.

## Check list
- [x] unit-tests written
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1a097fcffff9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.