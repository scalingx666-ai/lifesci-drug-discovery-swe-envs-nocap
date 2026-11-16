# Issue

**Title:** Raise error if model directory doesn't exist

## Description

The fix includes raising an error when the model directory doesn't exist on the system.

Logs after the implemented fix:

```python
(ersilia) ☁  ersilia-project  ersilia -v fetch eos9iyc --from_dir ./eos9iyc
From dir:  ./eos9iyc
17:38:05 | DEBUG    | Repo path specified: ./eos9iyc
17:38:05 | DEBUG    | Absolute path: /home/user/ersilia-project/eos9iyc
🚨🚨🚨 Something went wrong with Ersilia 🚨🚨🚨

Error message:

Model directory does not exist at the provided path. Please check the path and try again.
If this error message is not helpful, open an issue at:
 - https://github.com/ersilia-os/ersilia
Or feel free to reach out to us at:
 - hello[at]ersilia.io

If you haven't, try to run your command in verbose mode (-v in the CLI)
 - You will find the console log file in: /home/user/eos/current.log
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2961dfc3a2c5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.