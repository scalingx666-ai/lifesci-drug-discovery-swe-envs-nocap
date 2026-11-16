# Issue

**Title:** survminer: auto-generated tool wrapper (issue #1949)

## Description

This PR adds a new Galaxy tool wrapper for `survminer::ggsurvplot()`, which creates Kaplan-Meier survival curves from tabular survival data. The wrapper accepts user-specified column mappings for time, status, and optional grouping variables, with extensive customization options including confidence intervals, p-values, risk tables, cumulative events/censor plots, median survival lines, color palettes, and transformation functions. The implementation uses a `configfile` approach with Cheetah templating to generate the R script, keeping the complex conditional logic readable and maintainable. Five test cases cover grouped and single-group curves, confidence intervals with median lines, PDF output, and custom palettes. Generated files include the main `ggsurvplot.xml` wrapper, `macros.xml` with version tokens and citations, `.shed.yml` metadata, and a synthetic `test-data/lung.tsv` dataset.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dd9410515025`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.