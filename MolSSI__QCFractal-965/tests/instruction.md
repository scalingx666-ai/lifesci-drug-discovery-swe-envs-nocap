# Issue

**Title:** Switch to using threads in snowflake

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

Multiprocessing is just awkward. `fork` can have random issues due to mixing forking and threads (see https://discuss.python.org/t/switching-default-multiprocessing-context-to-spawn-on-posix-as-well/21868)

On the other hand, `spawn` (and `forkserver`) are slow and have other awkward requirements (you absolutely need to have any use of a snowflake under an `if __name__ == "__main__"` block).

So instead lets try threads. This seems to work just fine, although perhaps with some resource usage issues if being highly utilized (GIL and all that).

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b52e3ff45cd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.