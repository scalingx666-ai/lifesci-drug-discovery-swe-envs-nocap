# Issue

**Title:** Name the sparse AUMCall standard error and degrees of freedom consistently

## Description

`main` fails the parameter naming test added in the pretty-name cleanup: the sparse `aumcall_se` and `aumcall_df` were registered as "AUMC,all ..." on a branch that merged after that cleanup. They are now "AUMCall standard error" and "AUMCall degrees of freedom", like the other AUMC parameters.

## Testing
- Full test suite passes.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8fb4cf601428`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.