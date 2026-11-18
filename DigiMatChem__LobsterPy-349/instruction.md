# Issue

**Title:** `matplotlib` use non-interactive agg backend

## Description

Fix a previously added parameter as the original comment is a bit misleading, agg is the [recommended non-interactive backend](https://matplotlib.org/stable/users/explain/figure/backends.html):
> The last, Agg, is a non-interactive backend that can only write to files. It is used on Linux, if Matplotlib cannot connect to either an X display or a Wayland display.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f165c485cf3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.