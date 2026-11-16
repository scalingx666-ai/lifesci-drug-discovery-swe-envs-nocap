# Issue

**Title:** Port AtomicLocal integration to GPU

## Description

This PR ports the integration of the `AtomicLocal` form factors to the GPU.

In standard calculations, the instantiation of the `AtomicLocal` term in the `PlaneWaveBasis` is generally negligible. However, when ForwardDiff Duals are involved, this is an other story. In particular, for stress calculations on the GPU (not yet generally available, see ), this step becomes vastly more expensive than anything else.

For efficiency, the form factors are only calculated for a set of `G` vector norms, rather than for each individual `G`. With ForwardDiff Duals, 2 `G` vectors with the same value might differ in their partials and have a different norm. As a result, a lot more integrations must take place.

This PR introduces a special case for the GPU, where a `map!` kernel is launched over the `G` vector norms, and each GPU thread takes care of an integration on the atomic grid. This only triggers in the special case of UPF pseudos on the GPU.

Notes:
- This PR will drastically speed up stress calculations on the GPU. While the new function will also be used for the instantiation of a standard `PlaneWaveBasis`, its impact there will be smaller
- The `AtomicLocal` term will remain expensive on the CPU. Since everything else also gets more expensive, it is less of an obvious bottleneck in that case. However, I think it would be trivial to parallelize it over Julia threads
- Due to the complex dispatching taking place, and the fact that the `ElementPsp{<:PspUpf}` type is far from being `isbits`, I did not manage to come up with a single code to run on both CPU and GPU.
- The instantiation of the `Xc` term suffers from a similar problem, to be treated in a separate PR

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a1308a1fa8e6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.