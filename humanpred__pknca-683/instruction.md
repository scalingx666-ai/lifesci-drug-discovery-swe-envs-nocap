# Issue

**Title:** Add frac_unbound support to PKNCAconc() and pk.nca()

## Description

Description

This PR adds an optional frac_unbound argument to PKNCAconc(). When it is given, pk.nca() calculates parameters on total concentrations and again on unbound concentrations, and reports both. .

The NCA runs twice, and the results get a new first grouping column, frac_unbound, with the values "total concentration" and "unbound concentration".

Behavior

frac_unbound is a numeric value or a column name. Values must be greater than 0 and at most 1. NA is allowed where fraction unbound does not apply (for example, urine). Within a calculation interval, the values for a group must be all NA or all non-NA. A mix raises pknca_error_frac_unbound_mixed_na. The unbound run scales conc (and lloq, when present) by frac_unbound. Rows with NA are left out of the unbound run. Dense and sparse PK are both supported. For sparse data, each sample is scaled before the arithmetic-mean profile is built. A grouping variable named frac_unbound is rejected when frac_unbound is given (pknca_error_frac_unbound_group_name). Without frac_unbound, output is unchanged.

Files changed

R/class-PKNCAconc.R: new argument, validation, and the group-name check.
R/pk.calc.all.R: pk.nca() now calls pk_nca_calculate() (the existing calculation, moved unchanged) and, when frac_unbound is present, pk_nca_frac_unbound(). Adds the unbound-data and interval-check helpers.
R/prepare_data.R: frac_unbound is carried into the prepared concentration data.
R/class-PKNCAresults.R: frac_unbound is the first group column in getGroups() and group_vars().
NEWS.md, man/PKNCAconc.Rd: documentation.
tests/testthat/test-class-PKNCAconc.R, test-pk.calc.all.R, test-prepare_data.R: new tests.

Testing

test-pk.calc.all.R: total results match a run without frac_unbound; unbound cmax and auclast equal fu × total at a constant fraction; lloq scaling; mixed-NA error; urine-style NA rows get total results only; dense and sparse.
test-class-PKNCAconc.R: constructor validation and the reserved group name.
test-prepare_data.R: the column is carried only when used.
Full devtools::test() run: no failures from this change. Two pre-existing issues remain, both on the original upload as well: test-provenance.R fails because sessionInfo() output differs by environment, and test-half.life.R emits two expected-warning messages.
Manual check with a sample dense and sparse dataset: unbound values match fu × total where expected (for example, dense S01 unbound cmax 0.51 = 0.10 × 5.1). The example script is frac_unbound_example.R, and it runs without frac_unbound and with it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bdde0560b03a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.