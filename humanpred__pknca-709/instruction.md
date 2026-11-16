# Issue

**Title:** Join ordered-factor group columns whose levels differ

## Description

Group columns that are ordered factors with different levels in the conc data, dose data, intervals, or a normalization table made dplyr joins stop with "Can't join ... due to incompatible types". The common case was `update()` on results from `datasets::Theoph`, an nlme `groupedData` whose subsetting drops unused levels:

```r
d_conc <- Theoph[, c("Subject","Time","conc")]
d_dose <- dplyr::mutate(dplyr::summarise(dplyr::group_by(Theoph, Subject), Dose = Dose[1]*Wt[1]), Time = 0)
o_dose <- PKNCAdose(d_dose, Dose~Time|Subject)
o_nca <- pk.nca(PKNCAdata(PKNCAconc(d_conc, conc~Time|Subject), o_dose))
update(o_nca, PKNCAdata(PKNCAconc(subset(d_conc, !(Subject=="1" & Time>20)), conc~Time|Subject), o_dose))
```

## Fix
`unify_factor_join_keys()` gives both sides one set of levels before the join (the superset when one side's levels contain the other's, else the union with x's levels first). It is applied to the conc/dose and interval joins, the units-table conc/dose join, the date-time reference joins, `as.data.frame(filter_requested = TRUE)`, `normalize()`, and `summary()` by group.

## Tests
The Theoph update, the helper's level rules, each join site, and `summary(drop_group = character())` with ordered subjects whose levels differ between conc, dose, and intervals.

Stacked on `fix/impute-volume-duration`; this PR's diff is only this fix.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e8ecde260439`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.