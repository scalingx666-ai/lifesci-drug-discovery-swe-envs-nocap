# Issue

**Title:** Give calculation functions start and end on the interval's time scale

## Description

`pk.nca()` gave calculation functions `time` relative to the interval start, but `start`, `end`, and the group times on the original scale. For any interval not starting at 0, results that compare the two were wrong. With intervals 0-12 and 12-24 (doses at 0 and 12), the second interval gave:
- `ctrough` NA instead of 1.1;
- `cstart` 1.1 (the concentration at 24) instead of 1;
- `aumcint.last` 544 instead of the 154 that `aumclast` gives (and the `aumcint.*`/`aumcivint.*` family likewise).

## Fix
Every time given to a calculation function (`start`, `end`, `time.group`, `time.dose.group`, `time.sparse.group`) is now relative to the interval start, shifted in one place in `pk.nca.interval()`, so `start` is 0 and `end` is the interval duration. AUC, Cav, and the excretion rate are unchanged (they use differences). Imputation functions still receive the original times; the `add.interval.col()` help and the v08 and v80 vignettes now say which scale each gets.

**Contract change:** a parameter registered with `add.interval.col()` that reads `start` or `end` as an absolute time needs the same change. NEWS says so.

## Tests
- `ctrough` and `cstart` on 12-24.
- `aumcint.last` equals `aumclast`, and `aumcint.inf.obs` equals `aumcinf.obs`, for an interval starting at a later dose.
- AUCint and Cav are unchanged.
- A registered probe function checks the exact times every time source receives.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `362a9d01c88c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.