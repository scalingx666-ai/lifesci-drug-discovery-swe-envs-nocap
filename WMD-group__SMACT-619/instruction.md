# Issue

**Title:** Update outdated examples and tutorials

## Description

## Description

This PR updates all example and tutorial notebooks to work correctly with the current SMACT library, fixing outdated API calls, updating outputs, and clarifying explanations.   

## Changes

### Source code changes

**`smact/dopant_prediction/doper.py`**
- Added `pymatviz=False` to `plotting.periodic_table_heatmap`. Otherwise, nothing renders due to a deprecation warning.

### Notebook changes

**`docs/examples/elements_and_species.ipynb`**
- Updated cell outputs to reflect current library behavior (Fe oxidation state list changed)
- Fixed `Species` coordinate notation: `"4_n"` → `4` with an explanatory comment

**`docs/examples/filter.ipynb`**
- Updated cell outputs to reflect current library behavior (composition results changed)

**`docs/examples/validity.ipynb`**
- Added output demonstrating the `mixed_valence=True` behavior

**`docs/examples/lists.ipynb`**
- Fixed documentation formatting: replaced reST directive `` :mod:`smact` `` with plain backtick notation

**`docs/examples/oxidation_states.ipynb`**
- Clarify the definition of $P_{SA}$
- Updated cell outputs to reflect current library behavior

**`docs/examples/doper.ipynb`**
- Fixed outdated output formats of `material.get_dopants()`
- Fixed to show the actual plots of `plot_dopants`

**`docs/examples/distorter.ipynb`**
- Simplified `get_inequivalent_sites()` call — now takes the structure object directly instead of requiring manual extraction of lattice matrix, positions, and atomic numbers
- Removed unused `import numpy as np`
- Fixed typo: "more more recent studies" → "more recent studies"
- Updated cell outputs to reflect current library behavior

**`docs/examples/property_prediction.ipynb`**
- Updated filtering to apply `smact_validity` after `smact_filter`, with a comment explaining the difference between the two (broad vs. restricted ICSD24 oxidation state sets)
- Added missing cell outputs throughout the notebook

**`docs/tutorials/oxidation_states.ipynb`**
- Updated `neutral_ratios()` usage: the function now returns a single value instead of a tuple (`cn_e, cn_r = ...` → `cn_r = ...`)
- Updated outputs to reflect current results

**`docs/tutorials/smact_validity_of_GNoMe.ipynb`**
- Updated description of `smact_validity` to reflect that the Pauling electronegativity test and `mixed_valence=True` are available

**`docs/tutorials/structure_prediction.ipynb`**
- Updated Materials Project API import: `pymatgen.ext.matproj.MPRester` → `mp_api.client.MPRester`
- Added cell to set `MP_API_KEY` environment variable
- Updated outputs to reflect current results

**`docs/tutorials/crystal_space.ipynb`**
- Updated outputs to reflect current library behavior
- Replaced `fillna` for pandas df with `notna` to remove FutureWarning

**`docs/tutorials/crystal_space_visualisation.ipynb`**
- Added missing plot output image

**`docs/tutorials/smact_generation_of_solar_oxides.ipynb`**
- Removed `matminer.featurizers.conversions.StrToComposition`; replaced with direct `Composition` mapping
- Updated `neutral_ratios()` call (same tuple → single value change as above)
- Added `feature_calculators.set_n_jobs(1)` to allow users to configure parallel jobs

## Type of change

- [ ] Bug fix (non-breaking change which fixes an issue)

## How Has This Been Tested?

- [x] Re-executed all the updated notebooks end-to-end (except for `tutorials/smact_generation_of_solar_oxides.ipynb`, which was tested with a subset of possible compositions to avoid a lengthy end-to-end run.)
- [x] Ran all test cases via `make ci-local`

**Test Configuration**:

- Python version: 3.12.3
- Operating System: Linux (WSL2)

## Checklist

- [x] My code follows the style guidelines of this project
- [x] I have performed a self-review of my own code
- [x] I have commented my code, particularly in hard-to-understand areas
- [x] I have made corresponding changes to the documentation
- [x] My changes generate no new warnings
- [x] I have added tests that prove my fix is effective or that my feature works
- [x] New and existing unit tests pass locally with my changes
- [x] Any dependent changes have been merged and published in downstream modules
- [x] I have checked my code and corrected any misspellings


<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
## Summary by CodeRabbit

* **Documentation**
  * Refreshed many example and tutorial notebooks: updated example outputs and explanatory text, adjusted displayed examples, removed/cleaned large captured outputs, and harmonised kernel/runtime metadata.
* **Improvements**
  * Enhanced dopant-prediction visualisation with a redesigned periodic-table heatmap, improved numeric formatting and display.
* **Tests**
  * Updated tests to align with the new heatmap implementation mock targets.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e79878b17876`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.