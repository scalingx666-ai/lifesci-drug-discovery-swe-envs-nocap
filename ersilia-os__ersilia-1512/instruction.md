# Issue

**Title:** Clean up temp files from model containers

## Description

Related to #1511 

This PR introduces a neat way of removing temporary files specifically those found in `~/eos/sessions/session_xxxxx/_logs/tmp` (storing temporary container logs on the system storage). A new private method `_delete_temp_files` is added to the `PulledDockerImageService` class that cleans up these temporary files (and directories) before stopping and removing a model's container process. The method first lists the files and then removes them from within the container, this of course takes care of these files on the system storage as well.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5dc3e30f51e3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.