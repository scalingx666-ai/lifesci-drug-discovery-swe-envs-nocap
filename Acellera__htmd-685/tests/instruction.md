# Issue

**Title:** fixes bug in preparation that pandas does not like

## Description

This solves the issue with pandas 0.23. I'm still not sure why it didn't error on py3.5 but it did on py3.6 (maybe pandas got updated in between one build and the other? that's unlucky), but ensuring that the value `ov` is already a list when `append=True` makes sense.

Testing locally with updated pandas 0.23 pass (while fail on 0.22). Let's hope they pass on Travis too.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f3728cc075b5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.