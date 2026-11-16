# Issue

**Title:** Interval support functions: add/remove impute

## Description

Contributes to solve #379 

New interval supporting functions acting to add/remove imputations from the impute column in `PKNCAdata$intervals`


### Add imputation
`interval_add_impute(data, target_impute, after = Inf, target_params = NULL, target_groups = NULL)`

impute is the imputation character string to add, matching the behavior of PKNCAdata()
after follows similar behavior to the after argument of base::append(); 0 indicates it will be added as the first imputation method; Inf (or any number greater than the number of methods currently specified) indicates that it will be added as the last imputation method;
If there is already an imputation:

the imputation will be separated by commas (i.e. strsplit(current_impute, split = "[, ]"))
the new imputation will be added at the correct place (defined by after), and
The final imputation method will be put back together separated by commas (i.e. vapply(X = new_impute, FUN = paste, collapse = ",", FUN.VALUE = ""))

### Remove imputation
`interval_remove_impute(data, target_impute, target_params = NULL, target_groups = NULL)`

split any imputation from the intervals and remove it
warn if the imputation was not found in any of the intervals

> Note
For both functions optional arguments can be used to specify on which parameters (target_param, character vector) or at which specific interval rows (target_groups; list of column names and values) the action takes place

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `46ec28b038e3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.