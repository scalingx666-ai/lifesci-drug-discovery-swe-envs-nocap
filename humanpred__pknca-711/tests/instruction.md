# Issue

**Title:** Preferred units when some unit sets need no conversion

## Description

`concu_pref` (or `doseu_pref`) with unit columns that differ between groups stopped `PKNCAdata()` with "arguments imply differing number of rows: 1, 0" when a group was already in the preferred units. Repro: parent in mg/L and metabolite in ng/mL, with `concu_pref = "mg/L"`.

## Fix
Every unit set now has the `PPSTRESU`/`conversion_factor` columns, using its own units and a factor of 1 where it does not convert, as `pknca_units_table()` already does within one set.

## Tests
The units table and the `PPSTRES` values for both concentration and dose unit columns.

Stacked on `fix/units-join-group-types`; this PR's diff is only this fix.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `695c8e9cdcd2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.