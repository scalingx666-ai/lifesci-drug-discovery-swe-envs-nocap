# Issue

**Title:** Trim Galore: remove obsolete trim1 option and stabilize report tests

## Description

Combine the obsolete `--trim1` fix from #2027 with portable report tests in one `0.6.10+galaxy1` release, as requested in  PR #2027's original commit is retained as the parent of the report-test changes. .

Trim Galore removed `--trim1` in v0.6.8, but the wrapper still exposed and emitted it, causing `Unknown option: trim1`. The combined change removes that parameter and command interpolation, documents the two 3-prime clipping options, and retains #2027's new paired-end regression test for clipping one base from each mate.

The six full-report comparisons are replaced with shared assertions for selected adapters, read/base counts, quality trimming, filtering and paired-length validation. Exact occurrence counts require both mate reports; collection cases also check the unpaired-read cutoffs. Existing FASTQ comparisons remain in place. This avoids failures from Cutadapt/Python versions, allocated cores and tied adapter-candidate ordering. PR #2027's failed CI summary contained precisely these five report-only failures (indices 1 and 6–9); its lint job passed.

The separate commit `0338027e` fixes eight unqualified collection `format_source` references flagged by the newer linter and declares the existing reStructuredText help as `restructuredtext` (it had been labeled Markdown in #2027). There is one wrapper revision bump, inherited from #2027.

Validation:
- Current local `planemo lint` passes with no warnings; all 15 tests are recognized.
- CI-matched `planemo shed_lint --tools --ensure_metadata --urls --fail_level warn --recursive tools/trim_galore` passes with Planemo 0.75.47 and Galaxy tool-util 26.1.1; no checks skipped.
- Galaxy's assertion verifier accepts all six report fixtures and environment/replay cases and rejects all 74 deliberately altered result cases.
- Combined branch: `planemo test --biocontainers` **15/15 pass**, zero failures/errors/skips, using `quay.io/biocontainers/trim-galore:0.6.10--hdfd78af_2`. This includes #2027's clipping regression and all six changed report tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `19a59bad8913`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.