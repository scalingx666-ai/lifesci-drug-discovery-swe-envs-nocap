# Issue

**Title:** Bug Fix for Unix Systems

## Description

- ```subprocess.Popen``` call required a list of arguments instead of a string on Unix-based systems, therefore the command was ```.split()``` to form a list

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `da3aa5e852c2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.