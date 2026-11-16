# Issue

**Title:** Sparse AUMC

## Description

I added the sparse AUMC function along with five AUC-variant PK parameters. When running the tests, I encountered the following error: Failure (test-pk.calc.all.R:789:5): pk.nca can be run for each parameter independently (#473) all(is.na(param_res$result$PPORRES)) is not FALSE
actual: TRUE
expected: FALSE
The parameter mrt.sparse.last was not being calculated independently. To address this, I added the sparse-related parameters to test-pk.calc.all.R under non_pknca_covered_params: f, time_above, mrt.md.obs, mrt.md.pred,
sparse_auclast, sparse_auc_se, sparse_auc_df,
sparse_aumclast, sparse_aumc_se, sparse_aumc_df,
vss.md.obs, vss.md.pred, ceoi,
cl.sparse.last, mrt.sparse.last, vz.sparse.last,
vss.sparse.last, kel.sparse.last
Please let me know if this approach looks correct. After this update, the test results are:
[ FAIL 0 | WARN 4 | SKIP 0 | PASS 2264 ]
Remaining warning:
Warning (test-PKNCA.options.R:440:3): PKNCA.set.summary input checking reset = TRUE is not intended for general use; summary() may not work after resetting summary instructions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ee1b433a0efc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.