# Issue

**Title:** suggestions to NChooseK repair function

## Description

## Motivation

@LukasHebing I was looking at the LinearProjection and how it handles the repair with NChooseKConstraints and found results that were not intuitive to me.

In a nutshell, I consider a NChooseKConstraint over 6 inputs, with a min_count=2 and a max_count=3.
I consider the following candidate x:
`[[3.60200e-03 0.00000e+00 1.24000e-04 1.48000e-04 3.16161e-01]]`
`np.argsort(x): [[1 2 3 0 4]]`

With the following lower and upper bounds before repair:
`lb before repair [[0. 0. 0. 0. 0.]]`
`ub before repair [[0.46000001 0.47       0.28       5.         5.        ]]`

After the repair the bounds and candidate becomes:
```
lb after repair [[0.    0.    0.001 0.    0.001]]
ub after repair [[0.   0.47 0.28 0.   5.  ]]
repaired candidate
[array([-4.78402306e-28,  0.00000000e+00,  1.00000000e-03, -1.96578431e-29,
        3.16161000e-01])]
```
In my opinion something goes wrong here. I would expect the biggest components in the candidate to remain, so indices 0 and 4 in this case, with the min_value (1e-3) attributed to the one highest after that.
Basically I would expect the following to happen:

```
lower bound before repair [[0. 0. 0. 0. 0.]] upper bound before repair [[0.46000001 0.47       0.28       5.         5.        ]]
lower bound after repair [[0.001 0.    0.    0.    0.001]] upper bound after repair [[0.46000001 0.         0.         5.         5.        ]]
repaired candidate
[[ 3.60200000e-03  0.00000000e+00 -1.64712484e-29  1.48000000e-04
   3.16161000e-01]]
```

Do you agree with this, or am I missing some understanding here?

I made a suggestion to adjust the `_ub_correction` and `_lb_correction functions` that should give us the correct behavior. So far it is tested on up to two NChooseKConstraints but with disjoint subsets of the features. Not sure if it will also work if that is not the case, but also not sure if we would really want users to do this. Thoughts @jduerholt?

### Have you read the [Contributing Guidelines on pull requests](https://github.com/experimental-design/bofire/blob/main/CONTRIBUTING.md#pull-requests)?

Yes.

## Test Plan

Already incorporated a unit test with one NChooseKConstraint and ContinuousInputs. Will add more after some discussion if this is the right way to go.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8a503c474c17`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.