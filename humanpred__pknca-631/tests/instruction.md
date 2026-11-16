# Issue

**Title:** fix: make the subject validation in as_sparse_pk() actually assert

## Description

`R/sparse.R`'s `as_sparse_pk()` validated its `subject` argument with

```r
checkmate::check_vector(subject, any.missing=FALSE, len=length(conc), null.ok=FALSE)
```

and discarded the result. The `checkmate::check_*` family returns `TRUE` or an
error-message string rather than throwing, so this line was inert: a `NULL`,
wrong-length, or `NA`-containing `subject` passed silently into the sparse
covariance bookkeeping. Switching to `assert_vector()` with the same arguments
enforces the contract the `@param` documentation already states ("may not be
null").

The length check is deliberately left where it is, above the `!is.na(conc)`
masking, so it validates `subject` against the full input rather than the
post-filter subset.

## Two existing tests were relying on the lax behavior

`test_that("sparse_mean", ...)` and `test_that("moment means are calculated
correctly", ...)` each built a data.frame whose subject column was named `id`
and passed it through the single-argument form of `as_sparse_pk()`. That branch
reads `conc$subject`, which was `NULL` for those frames — so both tests had been
running the sparse pipeline with no subject identifiers at all. The inert check
was the only thing letting that through. Both now name the column `subject` and
exercise the real per-subject grouping they were written to test; their
assertions on the per-timepoint means are unchanged and still pass, since those
means do not depend on subject identity.

## New tests

`tests/testthat/test-sparse.R` gains a case covering `NULL`, wrong-length, and
`NA`-containing `subject`, each asserting the specific checkmate message. The
wrong-length case deliberately uses a `conc` vector containing an `NA` so that
it pins the check against the pre-filter length: if the assertion were later
moved below the masking, `subject = 1:5` against 6 concentrations (5 non-`NA`)
would start passing and the test would fail.

## Verification

`devtools::test()` reports `FAIL 0 | WARN 2 | SKIP 0 | PASS 4597`. Both warnings
are in `test-half.life.R:1028` and are unrelated to this change.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `56b48aacfe15`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.