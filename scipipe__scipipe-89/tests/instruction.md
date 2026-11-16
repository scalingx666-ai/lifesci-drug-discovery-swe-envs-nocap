# Issue

**Title:** Hash SubStream IP Paths for TempDir

## Description

Currently, the TempDir hashing does not take into account any information from SubStreams. If a Process has all of its inputs defined by a SubStream and no outputs (for example `echo := wf.NewProc("echo", "echo {i:in|join: }")`), then the TempDirs are not unique and the workflow errors.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7ac8c31a07af`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.