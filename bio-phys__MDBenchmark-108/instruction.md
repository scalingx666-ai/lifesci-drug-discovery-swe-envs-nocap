# Issue

**Title:** Update plot style

## Description

.

Changes made in this pull request:
- Added option to set the plot DPI via `--dpi`.
- Added option to set the plot font size via `--font-size`.
- Added option to hide the linear scaling fit via `--no-fit`.
- Added saner defaults for `ylim`.
- Added custom `xticks` and `yticks` depending on the number of nodes/cores used and the benchmarks' performance.
- `xtick` steps can be overwritten with the option `--xtick-step`.
- Added a watermark (text: `MDBenchmark`) to the top left of the plot. It's added to every plot by default, but can easily be switched off with `--no-watermark`.

PR Checklist
------------
 - [x] Added changelog fragment in  `./changelog/` ([more information](https://github.com/bio-phys/MDBenchmark/blob/master/DEVELOPER.rst#using-towncrier))?
 - [x] Issue raised/referenced?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9c9a97dd8170`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.