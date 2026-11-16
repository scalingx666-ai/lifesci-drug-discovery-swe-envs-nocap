# Issue

**Title:** Support optional smooth realspace cutoffs

## Description

Realspace cutoffs previously acted as step functions, causing discontinuities when atom distances crossed cutoff boundaries. This adds opt-in smooth cutoff widths for two- and three-body dispersion so energies, gradients, and stress tensors transition continuously near the cutoff.

- **Core cutoff model**
  - Added `width2` and `width3` to `realspace_cutoff`.
  - Added a quintic smoothstep switch for cutoff tapering.
  - Keeps existing behavior unchanged when widths are unset or non-positive.

- **Dispersion evaluation**
  - Applied smooth switching to two-body and ATM three-body dispersion.
  - Included product-rule terms in analytic gradients and virials.
  - Applied the same smoothing to pairwise-resolved two- and three-body energies.

- **API exposure**
  - Added C API setters for realspace cutoffs, including smoothing widths.
  - Stored cutoff configuration on the C API model handle for dispersion, pairwise, properties, and numerical Hessian entry points.
  - Added Python `DispersionModel.set_realspace_cutoff(...)`.
  - Added ASE `realspace_cutoff` support for `disp2`, `disp3`, `cn`, `width2`, and `width3`.

- **Documentation and coverage**
  - Documented smooth cutoff options in the C and Fortran API references.
  - Added focused Fortran, C, and Python coverage for smooth cutoff behavior and pairwise consistency.

Example:

```fortran
type(realspace_cutoff) :: cutoff

cutoff = realspace_cutoff( &
   disp2=60.0_wp, disp3=40.0_wp, cn=30.0_wp, &
   width2=5.0_wp, width3=5.0_wp)

call get_dispersion(mol, model, param, cutoff, energy, gradient, sigma)
```

```python
model.set_realspace_cutoff(
    disp2=60.0,
    disp3=40.0,
    cn=30.0,
    width2=5.0,
    width3=5.0,
)
```

> [!WARNING]
>
> <details>
> <summary>Firewall rules blocked me from connecting to one or more addresses (expand for details)</summary>
>
> #### I tried to connect to the following addresses, but was blocked by firewall rules:
>
> - `dl.google.com`
>   - Triggering command: `/usr/lib/apt/methods/https /usr/lib/apt/methods/https` (dns block)
>
> If you need me to access, download, or install something from one of these locations, you can either:
>
> - Configure [Actions setup steps](https://gh.io/copilot/actions-setup-steps) to set up my environment, which run before the firewall is enabled
> - Add the appropriate URLs or hosts to the custom allowlist in this repository's [Copilot coding agent settings](https://github.com/dftd4/dftd4/settings/copilot/coding_agent) (admins only)
>
> </details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6b80189ae840`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.