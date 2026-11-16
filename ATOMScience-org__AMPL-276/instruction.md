# Issue

**Title:** Update plotting contexts

## Description

I found [this function](https://seaborn.pydata.org/generated/seaborn.plotting_context.html) that can automatically set the plotting context (changing font size, etc) for a single plot and leave the rest unchanged: 
```
with sns.plotting_context("talk"):
    sns.lineplot(x=["A", "B", "C"], y=[1, 3, 2])
```
So I added this to several plots in perf_plots() to make them prettier without changing a person's entire notebook plotting context. They look good on my version of jupyter lab, hopefully they look good on others' too.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ed92c46647a5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.