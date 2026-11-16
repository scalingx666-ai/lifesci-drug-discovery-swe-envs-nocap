# Issue

**Title:** Fix `delete_gcp_api` pointer type

## Description

Hi devs!

The current deallocation function `delete_gcp_api` seems deleted a wrong type, potentially causing segfault. This simple PR can fix this problem.

This PR is also related to  when we are testing our rust's dftd3 wrapper.

## Code to reproduce the problem

The following code can give segfault. the `GeometricCounterpoise` must be called a second time to reproduce this problem.
Perhaps different computing devices may give different behavior on this. The segfault at least happens to my PC.

```python
import numpy as np
from dftd3.interface import GeometricCounterpoise

numbers = np.array([1])
positions_bohr = np.array([[0.0, 0.0, 0.0]])

gcp = GeometricCounterpoise(numbers, positions_bohr, method='pbeh3c')
print(gcp.get_counterpoise(grad=False))
# Must run a second time to get the segfault
gcp = GeometricCounterpoise(numbers, positions_bohr, method='pbeh3c')
print(gcp.get_counterpoise(grad=False))
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a463a624791d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.