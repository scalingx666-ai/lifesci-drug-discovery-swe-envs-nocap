# Issue

**Title:** Preserve implicit hydrogens in polarizability calculations

## Description

At base `6903673ce8`, calculating effective polarizability for ethanol's first carbon changes the molecule's implicit hydrogen counts from `[3, 2, 1]` to `[3, 0, 0]`. The five hydrogen-preparing `Polarizability` entry points leave `[0, 0, 0]` because their temporary containers share the caller's atoms.

Count implicit hydrogens directly in all five paths. Atom factors include their hydrogen neighbors, molecular mean polarizability adds 0.387 per implicit hydrogen, and effective polarizability weights each hydrogen one bond beyond its parent. Preserve the existing cutoff and unreachable-distance weights, including weight 4 for distance -1. Read-only shortest paths replace the flag-writing breadth-first helper, and the descriptor's one-atom restore is removed. Calls with `addExplicitH=false` retain their numerical behavior.

Calculations no longer clone, configure atom types, infer hydrogen counts, or create hydrogen atoms. Aromaticity and hydrogen counts must be prepared beforehand; unset counts are treated as zero. This changes results for inputs that previously relied on automatic hydrogen assignment, including calls through the atomic descriptor and legacy ionization tool. BCUT and Autocorrelation already prepare explicit hydrogens and use the unchanged explicit-only calculation.

Distance matrices index every atom present in the supplied container, including existing explicit hydrogens. Implicit hydrogens need no additional rows or columns. Expanded matrices remain usable when they preserve the original atom indices.

Tests retain the non-mutation regressions and restored ethanol matrix test. Comparisons with explicit-hydrogen copies cover aromatic and charged atoms, mixed explicit and implicit hydrogens, phosphorus, disconnected components, both matrix sizes, and cutoffs -1, 0, 1, 2, 3 and 100. Separate checks cover unset counts and `addExplicitH=false`. Tests check atom and bond counts, hydrogen counts, and flags.

Checked on Linux (JDK 21, Maven): with production code at `6903673ce8`, the new non-mutation tests fail. With this change, `EffectiveAtomPolarizabilityDescriptorTest` passes all 18 tests, `tool/charges` 70 (six existing skips) and `descriptor/qsaratomic` 381. The other modules that call `Polarizability` also pass: `descriptor/qsarmolecular` (1,458 tests, 54 existing skips) and `legacy` (1,411, seven existing skips); that run predates the final distance-matrix correction, which only changes the `addExplicitH=true` matrix path none of them use.

Prepared with AI assistance (Claude Code and OpenAI Codex).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

https://claude.ai/code/session_01JfvcPZyKcKQUG9fQGYfRMw

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6903673ce8da`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.