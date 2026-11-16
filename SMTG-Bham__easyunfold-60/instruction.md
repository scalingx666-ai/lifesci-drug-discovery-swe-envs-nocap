# Issue

**Title:** Fix eff mass plotting w custom inputs

## Description

This PR contains a number of fixes and improvements:
- Fixes `plot_effective_mass_fit` (i.e. `easyunfold unfold effective-mass --plot-fit`) when custom effective mass fitting options (such as `manual-extrema` or `extremum-eigenvalue`) are used
- Fixes `plot_effective_mass` (i.e. `easyunfold unfold effective-mass --plot`) when custom effective mass fitting options (such as `manual-extrema` or `extremum-eigenvalue`) are used.
- Improved default choice of `xwidth` in `plot_effective_mass`
- Some docs updates to mention the effective mass plotting capabilities, with some tips
- Miscellaneous fixes and code streamlining

Tested using @Iamkeli's data. E.g. in a case where the CBM is filled (to the point where the bands appear a bit discontinuous around 1.5 eV above the CBM), the auto-band-edge detection doesn't work. But using the `extremum-eigenvalue` option allows the fitting to be performed as desired:
```
> easyunfold unfold effective-mass --plot --extremum-eigenvalue 5.41 --npoints 10

Loaded data from easyunfold.json
Band extrema data:
  Kpoint index  Kind      Sub-kpoint index    Band indices
--------------  ------  ------------------  --------------
             0  CBM                      0             289
           162  CBM                      0             289
             0  VBM                      0             289
           162  VBM                      0             289

Electron effective masses:
  index  Kind      Effective mass    Band index  from                      to
-------  ------  ----------------  ------------  ------------------------  ------------------------
      0  m_e                0.303           289  [0.0, 0.0, 0.0] (\Gamma)  [0.0, 0.0, 0.5] (A)
      1  m_e                0.214           289  [0.0, 0.0, 0.0] (\Gamma)  [0.0, 0.5, 0.0] (M)
      2  m_e                0.217           289  [0.0, 0.0, 0.0] (\Gamma)  [-0.333, 0.667, 0.0] (K)

Hole effective masses:
  index  Kind      Effective mass    Band index  from                      to
-------  ------  ----------------  ------------  ------------------------  ------------------------
      0  m_h                0.303           289  [0.0, 0.0, 0.0] (\Gamma)  [0.0, 0.0, 0.5] (A)
      1  m_h                0.214           289  [0.0, 0.0, 0.0] (\Gamma)  [0.0, 0.5, 0.0] (M)
      2  m_h                0.217           289  [0.0, 0.0, 0.0] (\Gamma)  [-0.333, 0.667, 0.0] (K)
Generating spectral function plot for visualising detected band branches...
```
(In this case the "hole effective masses" are irrelevant as we have specified the CBM eigenvalue)

<img width="800" alt="image" src="https://github.com/user-attachments/assets/1adba26d-72e3-4f70-9197-43346fcf733f" />

For reference; `easyunfold unfold plot --emax 6 --dos vasprun.xml.gz --eref 5.45`:
<img width="1000" alt="image" src="https://github.com/user-attachments/assets/ba26ee94-d0a6-467c-ac51-b772e488cb5c" />


<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
## Summary by CodeRabbit

- **Documentation**
	- Updated guides and tutorials with clearer instructions for inspecting detected bands and output figure customization, including additional tips for extended plot customization.
	- Improved clarity in the `example_mgo.md` documentation regarding band structure analysis and command usage, including a new warning section for corrupted files.
	- Corrected formatting in the `example_nabis2.md` documentation for consistent command-line instruction presentation.
- **New Features**
	- Added a new tip section in the tutorial for various plot customization and analysis tools.
	- Introduced a reference energy option for effective mass plots, improving data visualization and fitting for both electron and hole analyses.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `998f9ca95118`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.