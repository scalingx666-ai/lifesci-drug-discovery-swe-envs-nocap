# Issue

**Title:** Reduce code duplication in `_p_flip_1_to_0`

## Description

In #185, the `_p_flip_1_to_0` function was updated with the goal of having it be symmetric with the `_p_flip_0_to_1` function.

However, there are some corner cases that are not symmetric yet, such as the following:

```python
>>> from qiskit_addon_sqd.configuration_recovery import _p_flip_0_to_1, _p_flip_1_to_0
>>> _p_flip_1_to_0(0.1, 0.3)
0.0077777777777777776
>>> _p_flip_0_to_1(0.9, 0.7)
0.007777777777777777
>>> _p_flip_1_to_0(0, 0.3)
0.99
>>> _p_flip_0_to_1(1, 0.7)
0.006999999999999999
```

This PR changes `_p_flip_1_to_0` to simply call `_p_flip_0_to_1` with the appropriate parameters, which simplifies (don't repeat yourself) and fixes the above discrepancy.  The output following this change is:

```python
>>> from qiskit_addon_sqd.configuration_recovery import _p_flip_0_to_1, _p_flip_1_to_0
>>> _p_flip_1_to_0(0.1, 0.3)
0.007777777777777777
>>> _p_flip_0_to_1(0.9, 0.7)
0.007777777777777777
>>> _p_flip_1_to_0(0, 0.3)
0.006999999999999999
>>> _p_flip_0_to_1(1, 0.7)
0.006999999999999999
```

This change also .

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3172810249e3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.