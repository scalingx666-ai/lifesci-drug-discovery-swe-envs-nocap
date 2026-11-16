# Issue

**Title:** Query LibXC exact-exchange parameters by default for composed functionals

## Description

Till now, it has been gloriously easy to shoot oneself in the foot when using functionals from Libxc in Psi4 directly by forgetting to add the magical `use_libxc = True` key in the functional definition. For example, calling `hyb_gga_xc_b3lyp` directly without `use_libxc = True` leads to Psi4 only using the semi-local part, which is missing the 20% of exact exchange, and ridiculously large errors in energies and properties.

This PR makes the default behavior of Psi4 sane: when using a functional from Libxc, one should always use its exact exchange parameters. The expert route to turn off exact exchange is the one that should be gated behind the extra keyword.

## AI Summary

A hybrid exchange component listed in `x_functionals` had its exact-exchange parameters read from LibXC only when the definition carried `"use_libxc": True`. That is an unsafe default — a hybrid was silently run as a pure semilocal functional.

This makes querying LibXC the default: `use_libxc` now defaults to `True`, and `"use_libxc": False` is the per-component opt-out. When an opt-out discards exact exchange that LibXC declares for the component, a prominent warning is printed, since that quietly yields a different functional — noting whether the semilocal part is used alone or the definition's manual `x_hf` values are used in its place.

The parameters are only marked used when they are actually nonzero, so a plain semilocal component paired with an explicit `x_hf` block (B2PLYP, PBE0-2, the DSD-* functionals, ...) is left untouched.

## Change

A single hunk in `dft_builder.py`:

```python
if x_params.get("use_libxc", True):
    libxc_hf = x_func.query_libxc("XC_HYB_CAM_COEF")
    if libxc_hf["ALPHA"] != 0.0 or libxc_hf["BETA"] != 0.0:
        x_HF.update(libxc_hf)
        x_HF["used"] = True
        x_func.set_alpha(1.0)
```

plus a one-line docstring correction for the `use_libxc` default.

## Compatibility

- The 21 built-in hybrids that carried `"use_libxc": True` are unchanged (the flag is now redundant but harmless).
- The 29 double-hybrids that combine a pure semilocal X component with a manual `x_hf` alpha are unchanged: the queried parameters are zero, so nothing is marked used and the `x_hf` alpha is preserved.
- Custom functionals that used a hybrid LibXC exchange component *without* the flag (relying on the old default-off) now correctly pick up its exact exchange.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dad649708e24`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.