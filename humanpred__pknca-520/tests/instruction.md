# Issue

**Title:** Parameter formulas on website

## Description

I needed to think a bit out of the box for this one and implement something semi-automatized. 

- `add.interval.col` will optionally accept a `formula` arg in LaTeX
- the script `data_raw/write_parameters-available_md.R` generates the website with the table
- when the site is build the table is included as an article "Parameters Available"

let me know what you think. Also, you have more knowledge so it would be nice if you can do a quick review of the formulas I populated. Although I guess that they can always keep being corrected.

Feel also free to commit/push changes if easier

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2359ae7a8225`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.