# Issue

**Title:** Drop missing concentrations in superposition() before calculating

## Description

.

`superposition()` stopped with `NA/NaN/Inf in 'x'` on concentration data containing `NA`, while the same data passed straight to `pk.calc.half.life()` worked.

`check` in `pk.calc.half.life()` gates two different things: input validation, and the `clean.conc.blq()` call that removes `NA`. `superposition()` passed `check = FALSE` because it already validates its own inputs — and silently lost the cleaning too. It is the only caller that does this.

The same unfiltered `NA` caused a second crash: with an `NA` among otherwise-zero concentrations, the all-zero shortcut `if (all(conc == 0))` raises `missing value where TRUE/FALSE needed`. It would also have propagated through `interp.extrap.conc()` into the returned profile.

Cleaning `conc`/`time` once covers all three, because everything downstream reads them.

`clean.conc.na()` is used rather than `clean.conc.blq()`: superposition interpolates through BLQ values and must keep them, and the NA-only cleaner keeps the `conc.na` option working so a numeric setting substitutes instead of dropping. The cleaning is placed after the `check.blq` guard, which still needs to see a leading `NA` and reject it.

## Testing

Four assertions covering the reprex (pinned against the hand-filtered equivalent and against the exact value at t=0), the all-zero shortcut, and the `conc.na` substitution branch. Reverting the fix makes the new test fail with the issue's exact error.

3317 tests pass, 0 failures.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7954f5d1310b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.