# Issue

**Title:** Fix three copy-paste / wrong-constant bugs

## Description

- path_manager: use LW_PLATEAU (not ZORDER_PLATEAU) as line width for merged plateau half-bars (affects both plateau_left and plateau_right)
- path_manager: fix _get_whitespace_cover_width to subtract margins["y"][0] instead of margins["x"][0] when computing the y-range for the cover rectangle height
- layout_manager: correct the parameter name string passed to validate_numeric_sequence for extra_y_margin ("extra_x_margin" → "extra_y_margin") so that validation error messages name the right argument

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bbf4236c8ce6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.