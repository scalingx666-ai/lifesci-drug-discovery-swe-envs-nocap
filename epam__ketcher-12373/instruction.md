# Issue

**Title:** Backmerge: #11889 – Bonds in atomic structures behave as targets for a new connection in macromolecules mode

## Description

## How the feature works? / How did you fix the issue?

Backport of #12094 to `release/3.21`. Related issue: #11889. The fix was also backported to `release/3.20` in #12256.

While drawing a connection in Macro Flex/Snake mode, atomic bonds no longer intercept pointer events or show hover highlighting. Atom targeting remains available. Bond interaction is restored when drawing ends or is cancelled, including tool switching and editor destruction.

Includes 22 Bond tool unit tests and a CSS pointer-events regression test.

The Playwright regression is excluded, matching its removal from master in #12259. It remains in the `release/3.20` backport.

**CI fixes:**

- Updated Next.js and the lockfile to resolve the critical npm audit findings.
- Updated two Popup screenshot tests and their Linux baselines to exclude unrelated toolbar content from the captures.

## Check list
- [x] unit-tests written
- [ ] e2e-tests written
- [x] documentation updated
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [x] base branch (master or release/xx) is correct
- [ ] task status changed to "Code review"
- [x] reviewers are notified about the pull request

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a22256ffb5a3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.