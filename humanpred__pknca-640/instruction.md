# Issue

**Title:** feat(be): heteroscedastic fits, covariates, and a descriptive mode

## Description

be_assess(), be_compare(), and be_fit_models() gain three options so that
the treatment-comparison engine can replace nca.reporter's
model_compare_nca() and cover food-effect and DDI comparisons:

- heteroscedastic = TRUE fits treatment-specific residual variances:
  nlme::lme() with varIdent(~ 1 | .trt) for repeated measures and a new
  nlme::gls() path (model_type = "gls") for parallel designs.  The nlme
  path accepts non-replicated designs and several test levels when
  reference scaling is off; the full-replicate requirement stays when
  scaling is on.  lmer() only takes fixed prior weights, so combining it
  with heteroscedastic = TRUE is an error.
- covariates adds columns as additive fixed effects on every model path,
  carried by be_dataset() as .cov_<name> columns.  Missing, constant, and
  aliased covariates are errors; with an intra-subject-contrast regulator
  a warning says they affect only the geometric means.
- regulator = "descriptive" returns the ABE estimates with no limits,
  criterion, or pass column, and a caption saying no decision was applied.

Fixes found on the way, needed for parallel data:
- The fixed-effects ratio put subject in as a fixed effect even with one
  observation per subject, so every parallel design failed with a
  subscript-out-of-bounds error.  Parallel designs also drop the sequence
  term, which is the treatment arm there.
- Intra-subject contrasts are reported as missing for parallel data
  instead of aborting; be_table() still errors if an ISC regulator needs
  them.
- emmeans contrasts are named by test level and matched exactly; the
  previous substring match could pick another level's contrast.
- nlme within-subject variances carry the design-based ANOVA degrees of
  freedom, as be_within_var() does, so the NTID ratio bound is no longer
  always missing with model_type = "nlme".

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `de98a0521f62`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.