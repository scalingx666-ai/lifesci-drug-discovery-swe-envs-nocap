# Issue

**Title:** fix(be): follow the FDA guidance procedures for RSABE, NTID, and HVNTID

## Description

Brings the FDA reference-scaled frameworks in line with the FDA progesterone (2011) and warfarin (2012) guidance procedures, and stops silent data loss in the BE dataset preparation.

**Intra-subject contrasts (ISC):**
- Only subjects with every administration their sequence calls for are used.
- The estimate is the unweighted mean of the sequence means, with standard error and n − m df from the one-way model on sequence (SAS `model ilat = seq; estimate intercept 1 seq 1/m …`).
- Period effects no longer enter the ratio or its interval.

**Within-subject variance:**
- `be_within_var(model_type = "isc")` gives the guidance estimator, s2wR = Σ(D − D̄_seq)² / (2(n − m)), computed as `lm(log ~ subject + sequence:period)`.
- The FDA frameworks use it. It equals the EMA ANOVA for TRTR/RTRT and differs for TRR/RTR/RRT.

**Unscaled 80.00–125.00% criterion** (RSABE when swR < 0.294, NTID, HVNTID):
- Uses the guidance mixed model (`RANDOM TRT/TYPE=FA0(2)`, `REPEATED/GRP=TRT`, `DDFM=SATTERTH`), fit by REML in the new `R/bioequivalence-fda-mixed.R`.
- Satterthwaite df come from the analytic information on the Cholesky (FA0) scale.
- Fitting is blockwise by subject, so large studies stay fast.
- Each `be_assess()` row shows the ratio and interval its decision used.
- If the model can't be fit, `be_extract_param()` reports why in `model_error`, and only a decision that needs the unscaled criterion stops.

**`be_dataset()`:** stops on missing subject, sequence, period, or treatment values in analyzed rows, and on subjects with more than one sequence. Previously the model fits dropped those rows silently while `n` still counted them.

**Verification:**
- Pinned values come from a literal transcription of the guidance SAS code.
- With complete data the mixed model reproduces the ISC exactly with n − 2 df.
- Estimates and SEs match nlme where it converges.
- Degrees of freedom match a dense numerical-derivative computation, and the analytic derivatives match finite differences.
- Every error path has a test.
- R CMD check: 0 errors, 0 warnings.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6e5527228b8a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.