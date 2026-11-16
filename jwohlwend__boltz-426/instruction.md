# Issue

**Title:** Fix over-eager skip logic in filter_inputs_structure

## Description

### Description
[filter_inputs_structure](cci:1://file:///c:/Users/T2430514/Downloads/boltz/src/boltz/main.py:317:0-360:19) tried to detect completed predictions by recursively
listing everything under `out_dir/predictions/`, causing any nested directories
or files to be mistaken for record IDs.  
The function now inspects only the **immediate sub-directories** of
`predictions/`, which represent actual prediction folders.  
This restores correct skipping behaviour and guarantees that legitimate,
unprocessed targets are not silently ignored.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aaef5025c487`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.