# Issue

**Title:** fix(be): stop on a confidence interval or estimate that cannot be estimated

## Description

## Summary

Several bioequivalence paths turned zero degrees of freedom into a NaN confidence interval, which every decision then reported as a silent FAIL. This PR stops with a typed error instead. It builds on `fix/be-endpoint-widening`.

## Changes

- **Contrasts.** The fixed-effects ANOVA contrast and the contrasts computed through emmeans stop with `pknca_error_be_contrast_no_df`. Examples: a 2x2 crossover of two subjects, a parallel study of one subject per arm, a 3x3 Williams design of three subjects.
- **gls with a one-observation treatment.** It stops before fitting. Its variance and Satterthwaite df are not identified; depending on row order the interval was NaN or 1e-147 to 4e150.
- **Within-subject variance.** A replicated formulation whose replicates leave no residual df was reported as "not replicated". `be_within_var()` now reports df 0 for it, and the decisions stop with `pknca_error_be_within_var_no_df`.
- **NTID and HVNTID** require both within-subject variances; a missing reference variance used to fail silently.
- **Every decision** stops with `pknca_error_be_estimate_not_finite` when an estimate it uses is missing or not finite. Examples: input to `be_table()`, or a sparse bootstrap without finite replicates. Health Canada's point-estimate rule needs only the ratio.
- **Class hierarchy.** These errors inherit from `pknca_error_be_not_estimable`, with the df errors under `pknca_error_be_no_df`.
- **`be_compare()`** raises the error when it stops every framework, instead of `pknca_error_be_no_frameworks`.
- **Leaked warning.** The within-subject variance is the residual mean square of the `lm()` fit (identical to `anova()`'s), so `anova()`'s "essentially perfect fit" warning no longer leaks.
- The intra-subject contrasts and the FDA mixed model already stopped on missing df.

## Testing

- Typed-error tests for each case: every input to `.be_check_contrast_df()`, the gls row orders, every decider's variance and finite-estimate checks, and the absence of NaN warnings.
- Full test suite and R CMD check pass.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3b52ccf82251`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.