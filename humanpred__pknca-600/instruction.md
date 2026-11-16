# Issue

**Title:** Finish the checkmate/rlang migration leftovers from #548

## Description

Three items were prepared while #548 was open but did not land before it merged.

Five rlang::abort() calls carrying `# nocov` are collapsed onto one line, so the marker is a trailing comment rather than a `# nocov start` / `# nocov end` bracket.  interpolate.conc.R drops from three bracketed regions to none.

The last two base stop() calls left by #548's sweep -- in prepare_data.R and time.above.R -- become classed rlang::abort() calls, and time.above.R's multi-argument message becomes a sprintf template so the text can be grepped for.

Redundant `.var.name` arguments are dropped where they repeat what checkmate already reports.  The fifteen that remain are kept deliberately: the thirteen in PKNCA.options.R would degrade to "Assertion on 'x'", prepare_data.R's would report `unlist(cols)`, and superposition.R's disambiguates a checkmate::assert() with two candidate checks.

Not covered here: R/bioequivalence.R and the conditions added by #588 to R/superposition.R both use base stop()/warning().  They arrived after #548's merge base and are a separate migration.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `75bcd4adc5e3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.