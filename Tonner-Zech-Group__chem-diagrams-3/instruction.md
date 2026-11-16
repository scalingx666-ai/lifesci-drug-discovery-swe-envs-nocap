# Issue

**Title:** Add missing tests and CHANGELOG

## Description

Tests added (107 total, up from 80):
- TestDrawPathValidation: mismatched x/y lengths, invalid linetype values and lengths, non-numeric data, duplicate path names, non-string path_name
- TestConstructorValidation: invalid style, wrong-length / non-numeric extra_x_margin / extra_y_margin, negative width_limit / figsize
- TestImagePlacement: add_image_in_plot (basic, named, framed, unframed, explicit width/height, returns-self), add_image_series_in_plot (stored by name, keyed by x, top/bottom/per-image placement, recalculates after add_numbers_* and set_xlabels), plus validation for mismatched lengths and invalid y_placement values

CHANGELOG.md documents the initial 0.0.1 release feature set following the Keep a Changelog format.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bbf4236c8ce6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.