# Issue

**Title:** Faster sparse AUC/AUMC variance for serial, batch, and complete designs

## Description

## Summary
When the animals form groups sampled at exactly the same times, with no time sampled in more than one group (serial sacrifice, batch, and complete designs), Holder's covariance within a group is the sample covariance.
- The variance of the sparse AUC (or AUMC), sum_i w_i ybar_i, is then sum_b s_b^2/n_b, where s_b^2 is the sample variance of the animals' weighted sums sum_i w_i y_i over the n_b animals of group b.
- The Satterthwaite degrees of freedom are (sum a_b)^2 / sum(a_b^2/(n_b - 1)) with a_b = s_b^2/n_b. For serial sacrifice this is equation 6a of Nedelman, Gibiansky, and Lau (1995).

These equal the general calculation, which builds matrices over every pair of measurements, so `var_sparse_auc()` with 100 animals at each of nine times drops from about 260 ms to 5 ms. Small data are as fast as before.

Designs where groups share a time, and times whose mean the BLQ rule set to zero (Holder's covariance centers on the stored mean), still use the general calculation. `var_sparse_auc()` and `var_sparse_aumc()` now share one helper.

## Testing
- New tests compare the group calculation with an independent matrix-form reference for serial, batch, and complete designs (AUC and AUMC), check the fallback for a shared time and a forced-zero mean, and check that a group of one animal gives `NA` as before.
- 240 random designs (serial, batch, complete, mixed, with and without forced-zero means) matched the previous code to 1e-12 (variance) and 1e-10 (df).
- Full test suite passes; `R CMD check` gives 0 errors and 0 warnings.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c1ec8c0bef33`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.