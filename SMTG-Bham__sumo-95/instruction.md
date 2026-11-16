# Issue

**Title:** Move `string_to_spin` function for API compatibility

## Description

Following on from issue #94 , I've moved the `string_to_spin` function (which accepts the `--spin` argument and converts to a pymatgen Spin object) from the `parser.add_argument` call (in which it was implemented as the `type` parameter) to just before the `get_plot` calls in `dosplot` and `bandplot`. The `type` parameter in  `parser.add_argument` (for `dosplot` and `bandplot`) is now just `str`, so the conversion of the `spin` argument via the `string_to_spin` function now takes place just before the `get_plot` calls in `dosplot` and `bandplot`. This ensures that the `spin` argument is correctly parsed and converted for both cli usage and for Python API usage of `dosplot` and/or `bandplot` (as was the issue in this case). I've also made the `string_to_spin` function capable of accepting `None` as an argument as well, so that it doesn't throw up an error if no spin is selected.

I've checked that both the cli and API implementations of `dosplot` and `bandplot` works as expected for all possible `spin` arguments (i.e. no selection, up or down) .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3f894ff262a7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.