# Issue

**Title:** ADD: show_file

## Description

![file](https://user-images.githubusercontent.com/4451957/28970085-29474264-78f5-11e7-98a8-b233e90e0ca4.png)

Note: Need to set `--NotebookApp.iopub_data_rate_limit`
```bash
jupyter notebook --NotebookApp.iopub_data_rate_limit=10000000
```

Also hide "show_structure_file" in README since "show_file" already include that.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f69db9751933`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.