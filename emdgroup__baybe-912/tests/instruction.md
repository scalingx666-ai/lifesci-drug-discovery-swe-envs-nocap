# Issue

**Title:** Forbid Excluded Permutation Dependencies

## Description

there is a small bug reported by @AVHopp 
```python
"""DiscretePermutationInvarianceConstraint inverts deduplication when dependencies.exclude=True.

Root cause: DiscreteFilteringConstraint.get_invalid (base class) returns the
*matching* rows when exclude=True and df.index.drop(matching) otherwise.
DiscretePermutationInvarianceConstraint._get_matching_rows calls
    self.dependencies.get_invalid(df.loc[inds_valid])
and drops the result from inds_valid, expecting dependency-duplicates back.
With exclude=True, get_invalid instead returns the canonical (non-duplicate)
rows, so the drop removes the keepers and retains the duplicates.
"""

import pandas as pd

from baybe.constraints.conditions import SubSelectionCondition
from baybe.constraints.discrete import (
    DiscreteDependenciesConstraint,
    DiscretePermutationInvarianceConstraint,
)

# Row 0: (X, Y) — canonical representative of the {X, Y} permutation class
# Row 1: (Y, X) — permutation duplicate; should be the only invalid row
df = pd.DataFrame(
    {
        "P1": ["X", "Y"],
        "P2": ["Y", "X"],
        "Gate": ["on", "on"],
    }
)

deps = DiscreteDependenciesConstraint(
    parameters=["Gate"],
    conditions=[SubSelectionCondition(selection=["on"])],
    affected_parameters=[["P1", "P2"]],
    exclude=True,  # triggers the inversion bug
)
perm = DiscretePermutationInvarianceConstraint(
    parameters=["P1", "P2"],
    dependencies=deps,
)

invalid = perm.get_invalid(df)
print("Expected invalid: [1]")
print("Actual invalid:  ", invalid.tolist())  # Bug: returns [0, 1]
```

- This PR forbids `exclude=True` for dependencies inside permutation constraints
- This is intended as a small hotfix that simply avoids this bad configuration, there is much work planned anyway for the two involved constraints #664 and #670 - in particular they should be decoupled at class level), so tis really not worth spending more time on this for the moment

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `acd989a6ca5d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.