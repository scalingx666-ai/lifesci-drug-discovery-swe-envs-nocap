# Issue

**Title:** #12261 - Refactor: Explicit/implicit Any type clean up from packages\ketcher-core\src\domain\serializers\sdf\sdfSerializer.ts file

## Description

## How the feature works? / How did you fix the issue?
(Screenshots, videos, or GIFs, if applicable)

Updated sdfSerializer.ts to use RegExpExecArray | null for the regex match and string[] for property chunks.
Removed the file-level no-explicit-any suppression; no new shared type was needed.

## Check list
- [ ] unit-tests written
- [ ] e2e-tests written
- [ ] documentation updated
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [x] base branch (master or release/xx) is correct
- [x] task status changed to "Code review"
- [ ] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `65e93b06f47b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.