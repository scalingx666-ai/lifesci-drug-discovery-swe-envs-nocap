# Issue

**Title:** Benchmarking with graph and Excel file

## Description

Benchmarking now works with multiple numbers of molecules and generates a CSV file, and Excel file of normalized results, and a PNG plot. Example files are attached.

Everything is run from the script `benchmark.sh`.

Cluster quality statistics are currently dummy values and will be fixed in the next pull request. Will also add customizable args for output paths.

[benchmark.xlsx](https://github.com/NVIDIA/cheminformatics/files/5784453/benchmark.xlsx)

![benchmark](https://user-images.githubusercontent.com/1757241/103957749-5fe7ef80-5119-11eb-93f7-a7d9e743120c.png)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8745eb324a75`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.