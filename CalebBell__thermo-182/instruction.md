# Issue

**Title:** fix: correct multi-liquid selection flag in pure-component flash

## Description

## What's wrong

In `thermo/flash/flash_utils.py`, six pure-component flash helpers set a selection flag from a count instead of a boolean:

```python
one_liquid = len(liquids)
...
if one_liquid:
    lowest_phase = liquids[0].to_TP_zs(T, P, zs)
else:
    # pick the phase with the lowest Gibbs energy
```

`len(liquids)` is truthy for any count greater than zero, so the `if one_liquid:` branch runs whenever there is at least one liquid phase, not just when there is exactly one. With two or more liquid phases, this skips the Gibbs-energy comparison entirely and always returns `liquids[0]`, regardless of which phase is actually stable. With zero liquids, it falls to the `else` branch, the phase list comprehension is empty, `lowest_phase` stays `None`, and the next line crashes calling `.fugacities()` on `None`.

Same pattern for `one_other = len(other_phases)` and `one_solid = len(solids)` in `TSF_pure_newton` and `PSF_pure_newton`.

## Fix

Make the flags actual booleans:

```python
one_liquid = len(liquids) == 1
```

applied to all six functions: `TVF_pure_newton`, `TVF_pure_secant`, `PVF_pure_newton`, `PVF_pure_secant`, `TSF_pure_newton`, `PSF_pure_newton`. This preserves the fast path for the single-phase case and correctly runs the Gibbs-energy comparison whenever there's more than one candidate phase.

## Testing

I wrote a standalone repro using lightweight fake phase objects (mocking `to_TP_zs`, `G`, `fugacities`, `dfugacities_dP/dT`) to isolate the selection logic from the full EOS/data stack, since these functions don't have dedicated unit tests. With two liquid phases passed in `liquids[0]` = high Gibbs energy, `liquids[1]` = low Gibbs energy, and gas fugacity matched to the low-Gibbs phase:

- On current `master`, `TVF_pure_secant` raises `fluids.numerics.SamePointError` because it locks onto `liquids[0]` (the wrong, high-Gibbs phase) and the solver never converges.
- With this fix, all four `TVF_pure_*`/`PVF_pure_*` functions correctly select the low-Gibbs phase and converge.
- A single-liquid case confirms the `len == 1` fast path is unaffected.

I also confirmed `git blame` shows this line unchanged since it was introduced in 2021.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3c2fa0cee476`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.