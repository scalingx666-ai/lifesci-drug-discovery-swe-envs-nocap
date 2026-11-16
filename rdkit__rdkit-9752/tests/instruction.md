# Issue

**Title:** Fix Postgres GiST KNN returning wrong nearest neighbours for bfp

## Description

`gbfp_inner_distance()` in `Code/PgSQL/rdkit/bfp_gist.c` is declared `static double` but ends with `PG_RETURN_FLOAT8(1.0 - similarity)`. On 64-bit builds that pass `float8` by value, this macro packages the distance's IEEE bit pattern as an integer `Datum`. Because the helper returns `double`, C then numerically converts that integer to a double: an intended bound of 0.2 becomes about 4.6 × 10¹⁸. The leaf-distance helper returns an ordinary double, so page bounds and row distances end up on incompatible scales. This bug was introduced in 2016 in #992 

PostgreSQL's GiST KNN search keeps unopened index pages and already-found rows in one priority queue, keyed by page-distance lower bounds and actual row distances. It must explore any page whose bound is smaller than the next row's distance before returning that row. With an inflated bound, it can instead return a row at distance 0.4 while postponing a page whose true bound is 0.2 and which contains a closer match. Preserving the relative ordering of page bounds does not preserve their ordering against rows.

On indexes with multiple leaf pages, this can produce wrong nearest neighbours with `LIMIT k`, and the returned rows can also be out of distance order. When all remaining page bounds are inflated, the scan drains the current leaf page's rows before opening another page, producing individually sorted page batches with possible downward jumps between them. 

When PostgreSQL uses the GiST index to supply the requested distance order, it trusts that order without adding a full sort to establish it. Threshold-filtered queries such as `WHERE fp % q ORDER BY fp <%> q` and cursors using an affected plan can therefore return incorrectly ranked matches too.

The fix is one line, `return 1.0 - similarity;`. The outer `gbfp_distance()` function already performs the required `PG_RETURN_FLOAT8(distance)` conversion. 

**Reproducer:** [knn-d1-repro.sql](https://github.com/user-attachments/files/33984452/knn-d1-repro.sql) is a single self-contained SQL script with 200 fixed molecules, a 4-page GiST index and one query. 

On RDKit 2026.09.1 / PostgreSQL 18.6, the unpatched build fails both checks: the index's best distance is 0.4762 vs a true 0.2667, and without `LIMIT` the true nearest neighbour comes back 57th of 200, with the distance dropping at each of the two leaf-page boundaries. Both checks pass with the fix.

**Regression test:** the new `bfpknn` test (`sql/bfpknn.sql`, data in `data/bfpknn_data`) runs the same molecules and query through `<%>` and `<#>` and compares the index top-10 with an exact scan. It fails without the fix and passes with it; the rest of the cartridge suite passes either way.

**Disclaimer:** The bug was discovered and verified using Claude Opus 5.5 in Claude Code under my guidance and review.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `01976e53e9a1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.