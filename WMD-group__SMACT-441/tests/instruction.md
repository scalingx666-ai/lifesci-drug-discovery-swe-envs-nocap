# Issue

**Title:** WIP: Support validity for mixed valence compounds

## Description

## Description

**This PR is WIP while we finalise the list of supported mixed valence elements**.

Added support for mixed valence compounds in the `smact_validity` function. The default behaviour of the function has not changed. For example:

```python
from smact.screening import smact_validity

smact_validity("Fe3O4")
# returns False

smact_validity("Fe3O4", mixed_valence=True)
# returns True
```

The algorithm is as follows:
1. If a composition passes the regular oxidation state checking, the function proceeds as normal.
2. If a composition cannot be made to charge balance we first check if it contains any elements that are known to result in mixed valence compositions. The choice of these elements was based on screening of the ICSD.
3. If so, we "expand" the composition to treat potential mixed valence element as separate species. For example, Fe3O4 would be treated as FeFeFeO4.
4. We then perform the oxidation state checking again using the expanded composition.

The algorithm will fail if the reduced formula does not support mixed valence elements due to limited multiplicity. For example, Cs2SbCl6, which contains Sb3+ and Sb5+. To overcome this, a future fix could be to add another option to repeat the composition up to a fixed number (i.e., Cs4SbSbCl12).
​	
This PR addresses #196 and #418.

## Type of change

- [x] New feature (non-breaking change which adds functionality)
- [x] This change requires a documentation update

## How Has This Been Tested?

Added a `test_smact_validity_mixed_valence` in `tests_core.py`.

## Reviewers

@Panyalak @dandavies99 

## Checklist

- [x] My code follows the style guidelines of this project
- [x] I have performed a self-review of my own code
- [x] I have commented my code, particularly in hard-to-understand areas
- [ ] I have made corresponding changes to the documentation
- [x] My changes generate no new warnings
- [x] I have added tests that prove my fix is effective or that my feature works
- [x] New and existing unit tests pass locally with my changes
- [x] Any dependent changes have been merged and published in downstream modules
- [x] I have checked my code and corrected any misspellings

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

* **New Features**
  * Added support for handling mixed valence elements in compound validity checks via a new option.
* **Tests**
  * Introduced tests to verify correct behaviour for compounds with mixed valence elements.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `515a369f3a79`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.