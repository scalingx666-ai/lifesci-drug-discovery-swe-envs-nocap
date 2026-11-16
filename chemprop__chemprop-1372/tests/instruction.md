# Issue

**Title:** Fix hpopt monitor mode for val_loss tracking metric

## Description

> [!NOTE]
> This PR was handled entirely by Qwen 3.6 27b running locally via `opencode` with @JacksonBurns' supervision

Use the criterion class's higher_is_better instead of the first metric's to determine monitor mode when tracking val_loss, matching the logic in train.py. Previously, using --metrics R2 would incorrectly set monitor_mode to 'max' for val_loss.

 

## Checklist
- [x] linted with flake8?
- [x] (if appropriate) unit tests added?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `add3209288ce`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.