# Issue

**Title:** salmon: update tool wrapper (issue #2093)

## Description

.

`salmonquantmerge` now accepts multiple datasets or a list collection through one `quants` input and produces one merged matrix. It preserves input order beyond ten samples and makes column names unique after normalization, without stealing an existing sample name. Identifiers beginning with a hyphen are kept as sample names rather than interpreted as CLI options.

The review fixes stage gene-level inputs as `quant.genes.sf`, retain Salmon's default `NA` for an unset missing value while accepting explicit zero, and fail if Salmon returns success without creating its output. The suite also declares Alevin's helper files for remote staging and fixes Markdown help rendering. The wrapper version is `1.10.3+galaxy1`.

Alevin's tiny test fixture includes one ambiguous UMI (`TTGACACCAT` in cell `GTCCTCATCACAATGC`). Independent runs with one and three workers can retain one or all eleven equally matching transcript targets; checking the 98-base read against all 322 reference transcripts confirms those eleven have 96 matching bases. The BFH test now accepts the two observed assignments while checking every other record and the full transcript/barcode tables exactly. Matrix checks allow cell ordering and this one ambiguous assignment to vary while requiring the expected cell and gene identities, 14 rows each summing to one UMI, and all unambiguous gene totals. The help documents this run-to-run variability.

Input compatibility: workflows using the old `quantfiles` repeat must reconnect their inputs to `quants`. Column names now come from dataset or collection element identifiers.

Validation: 21 local tool tests passed (13 quantification, five merge, three Alevin), along with two workflow tests verifying one merge job per collection, colliding identifiers, and a leading-hyphen identifier. Tool, Tool Shed, and workflow lint passed. Tests used the pinned Conda dependencies and Galaxy 26.1. Regression fixtures contain distinct known values, missing features, and an eleven-sample merge.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `db60013c3dd3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.