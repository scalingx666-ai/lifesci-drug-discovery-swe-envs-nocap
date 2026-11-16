# Issue

**Title:** Polynomial feature interaction kernel

## Description

Hi, now that we have kernels that work only on subset of features, it would be nice to also combine these kernels to include interactions amongst them. This can be done already but it is a bit tedious for higher-order interactions and quite inefficient since the kernels would be re-computed multiple times with the same inputs.

Essentially one could now replace

```
k1 = RBFKernel(features=["x1", "x2"])
k2 = MaternKernel(features=["x2", "x3"])
k3 = HammingDistanceKernel(features=["x4", "x5"])

k = AdditiveKernel(kernels=[
    ScaleKernel(base_kernel=k1),
    ScaleKernel(base_kernel=k2),
    ScaleKernel(base_kernel=k3),
    ScaleKernel(base_kernel=MultiplicativeKernel(kernels=[k1, k2])),
    ScaleKernel(base_kernel=MultiplicativeKernel(kernels=[k1, k3])),
    ScaleKernel(base_kernel=MultiplicativeKernel(kernels=[k2, k3])),
])
```

with

```
k = PolynomialFeatureInteractionKernel(
    kernels=[k1, k2, k3],
    max_degree=2,
)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f278f6d3463b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.