# Issue

**Title:** Realign volume and collection duration after imputation

## Description

When imputation adds or drops an observation, `pk.nca.interval()` replaced `conc`/`time` but kept the original `volume` and `duration.conc`, so R recycled them against the wrong samples with only a "longer object length" warning. A urine profile with `impute = "start_conc0"` and no sample at the interval start gave `ae` = 440 instead of 300; `end_conc_drop` gave `ae` = 660 instead of 260 and `volpk` = 10 instead of 6.

## Fix
The volume and duration follow their observations by time. An added observation was not collected, so it gets a volume of 0 (no amount, no volume) and no duration (no excretion rate), and the excretion parameters equal those of the collected samples.

**Overlap with open PR 678** (realigns `include_half.life`, `exclude_half.life`, and `lloq` in the same block): the two conflict textually. On merge, use PR 678's `obs_index` for `idx_orig` (this branch uses the same variable name and meaning), keep this volume/duration block, and extend PR 678's lost-index error to volume and duration so `ae` cannot silently become 0 when the index is lost.

## Tests
A plasma + urine profile with `start_conc0`, giving exact values for `ae`, `fe`, `volpk`, `ermax`, `ertmax`, `ertlst`, `erlst`, `erint`, and `clr.last`, with no warnings and no exclusions; and `end_conc_drop` on a urine profile.

Stacked on `fix/impute-na`; this PR's diff is only this fix.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `50ede06bbe25`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.