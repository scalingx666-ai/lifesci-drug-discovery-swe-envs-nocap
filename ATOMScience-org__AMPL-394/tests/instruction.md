# Issue

**Title:** Create unit tests for plotting, visualizations code

## Description

- Added `matplotcheck` to dev_requirements.txt. Use the `PlotTester` APIs to run plot assertion tests
- Added tests for the plot libraries. A few of them need to wait till the code refactor to allow the ax to be passed in or return for the tester to run assertions. The ones to do are like: 
   - diversity_plots.py
   - hyper_perf_plots.py

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5fe790068a44`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.