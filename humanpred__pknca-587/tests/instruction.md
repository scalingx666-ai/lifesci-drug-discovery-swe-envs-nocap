# Issue

**Title:** fix: forward per-run options into sparse AUC and AUMC calculations

## Description

.

`pk.calc.sparse_auc()` accepted `options` but dropped it, so per-`PKNCAdata` `options = list(conc.blq = ...)` had no effect on sparse AUC while the global option did. The options now forward into the mean-profile integration; `pk.calc.sparse_aumc()` had the identical defect and gets the identical fix. The `pk.nca()` wiring already mapped `options` correctly, so the per-run route now works end-to-end. Also corrects the `sparse_mean()` help to the actual strictly-more-than-50% BLQ zeroing rule (code unchanged).

Verification: results under default options are unchanged (all pre-existing exact-value expectations pass unmodified); new exact-value tests cover the per-run route, the global route (now agreeing), sparse AUMC, and the exactly-50% boundary — 58 pass in the sparse file, 637 in adjacent files.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `06193bb86b2e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.