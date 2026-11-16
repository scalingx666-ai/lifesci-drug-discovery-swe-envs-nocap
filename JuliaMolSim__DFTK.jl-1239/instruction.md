# Issue

**Title:** Add custom inner product support to CG solver

## Description

## Summary
Fixed test failures by importing `dot` function in cg.jl.

## Changes Made
- [x] Added `using LinearAlgebra: dot` import to cg.jl
- [x] This fixes the `UndefVarError: dot not defined` error that was causing test failures

## Root Cause
The `my_dot=dot` default parameter was referencing `dot` from LinearAlgebra, but it wasn't imported in the cg.jl file scope. While `dot` is available in the parent DFTK module, it needs to be explicitly imported in cg.jl for use as a default parameter value.

## Testing
The fix resolves the Newton algorithm test failures that were occurring because `solve_ΩplusK` (which calls `cg`) was unable to use the default `dot` function.

<!-- START COPILOT ORIGINAL PROMPT -->

<details>

<summary>Original prompt</summary>

>
> ----
>
> *This section details on the original issue you should resolve*
>
> <issue_title>Use k-weighted weighted dot product in cg</issue_title>
> <issue_description>See last comment in  Change CG to accept a custom dot product, and have the caller use weighted_ksum</issue_description>
>
> ## Comments on the Issue (you are @copilot in this section)
>
> <comments>
> </comments>
>

</details>

<!-- START COPILOT CODING AGENT SUFFIX -->

- Fixes JuliaMolSim/DFTK.jl#1238

<!-- START COPILOT CODING AGENT TIPS -->
---

✨ Let Copilot coding agent  — coding agent works faster and does higher quality work when set up for your repo.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `af5f56a0909f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.