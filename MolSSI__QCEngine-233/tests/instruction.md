# Issue

**Title:** added optional param for execute: exit_code

## Description

execute method returns False if retcode > exit_code

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Enable util.execute to return True when the return code > 0. This is useful for Unix utilities such as grep.  

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
Added optional param 'exit_code' (default 0) to 'execute' function.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `141fcc787206`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.