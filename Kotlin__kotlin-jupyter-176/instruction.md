# Issue

**Title:** Update Lets-Plot dependencies: api -> 1.3.0, lib -> 2.0.1

## Description

- Improved facets: [Facets demo](https://nbviewer.jupyter.org/github/JetBrains/lets-plot-kotlin/blob/master/docs/examples/jupyter-notebooks/facets.ipynb)
- Formatting tick labels on X/Y axis: [Formatting demo](https://nbviewer.jupyter.org/github/JetBrains/lets-plot-kotlin/blob/master/docs/examples/jupyter-notebooks/formatting_axes_etc.ipynb)
- Default "plot viewer" for JVM apps: `plot.show()` opens a Java Swing frame.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8f03f84198de`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.