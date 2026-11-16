# Issue

**Title:** Axis labels

## Description

Addresses #9 by providing: `--xlabel` and `--ylabel` options for _dosplot_; `--ylabel` and `--dos-label` for _bandplot_.

`--dos-label` looks a bit cramped right next to the legend there, so I'm happy to leave `None` as the default. This seems most useful with `--total-only`, if only there was a way to disable the legend.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b4a4211462ca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.