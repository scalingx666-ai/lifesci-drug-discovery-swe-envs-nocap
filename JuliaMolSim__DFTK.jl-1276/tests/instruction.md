# Issue

**Title:** Warm-start Sternheimer CG from non-interacting solution

## Description

- [x] Thread `δψ0` initial guess through `apply_χ0_4P` → `compute_δψ!` → `sternheimer_solver`
- [x] `sternheimer_solver`: `δψk0=zero(rhs)` keyword; uses `cg!(R(δψk0), ...)`
- [x] `compute_δψ!`: `δψ0=nothing` keyword; `if isnothing` block per k-point
- [x] `apply_χ0_4P`: `δψ0=nothing` keyword; `if` statement for occupied subset
- [x] `solve_ΩplusK_split`: `let` block returns `(δρ0, δψ0)`; passes warm start to final solve
- [x] Merged origin/master to resolve branch divergence (conflicts resolved in chi0.jl)

<!-- START COPILOT ORIGINAL PROMPT -->

<details>

<summary>Original prompt</summary>

>
> ----
>
> *This section details on the original issue you should resolve*
>
> <issue_title>Sternheimer CG should use a better starting point than zero</issue_title>
> <issue_description>And by that I mean the solution computed at the previous GMRES iteration. Similarly to how the primal problem reuses the previous eigenvectors as a starting point for the next iterative diagonalization.
>
> Note: in the default callbacks, CG iterations seem to be summed over bands, whereas LOBPCG iterations are not. This makes comparison difficult.</issue_description>
>
> ## Comments on the Issue (you are @copilot in this section)
>
> <comments>
> <comment_new><author>@antoine-levitt</author><body>
> Agreed on both points (we should store and reuse the previous solution, and we should average among kpoints).</body></comment_new>
> </comments>
>

</details>

<!-- START COPILOT CODING AGENT SUFFIX -->

- Fixes JuliaMolSim/DFTK.jl#1275

<!-- START COPILOT CODING AGENT TIPS -->
---

💡 You can make Copilot smarter by setting up custom instructions, customizing its development environment and configuring Model Context Protocol (MCP) servers. Learn more [Copilot coding agent tips](https://gh.io/copilot-coding-agent-tips) in the docs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2c6b4cbbecdf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.