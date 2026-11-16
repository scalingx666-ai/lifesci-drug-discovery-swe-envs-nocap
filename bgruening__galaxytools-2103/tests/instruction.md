# Issue

**Title:** agat: update tool wrapper (issue #2094)

## Description

.

The shared annotation output now uses `tool.output_format.selector`, so selecting GTF in the seven annotation-processing modes produces a dataset typed as GTF. The regression test checks both the datatype and the expected GTF content. Four existing tests now check the actual `annotation` output instead of a filtered-out `annotation_gff` output.

The review fixes also restore quoted staging paths, expand the allocated CPU count in the job's YAML configuration, and keep one default reference source. The wrapper version is `1.7.0+galaxy2`.

Validation: all 18 local Galaxy tool tests passed with AGAT 1.7.0 and Galaxy 26.1; tool and Tool Shed lint passed. Galaxy's output-format function was also checked directly: the old parameter path returns `gff3`, while the corrected path returns `gtf`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `db60013c3dd3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.