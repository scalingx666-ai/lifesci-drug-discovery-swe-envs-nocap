# Issue

**Title:** Switch to api 0.0.17-SNAPSHOT

## Description

- support for environment variable "LETS_PLOT_HTML_ISOLATED_FRAME" (Datalore integration)
- `isolatedFrame` parameter. Usage: `%use lets-plot(isolatedFrame=true)`
- LetsPlot.getInfo()

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6e0d7d92785d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.