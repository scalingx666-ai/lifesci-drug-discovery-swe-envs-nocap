# Issue

**Title:** Lazy instantiation

## Description

Minor to no speed improvement. Fair memory allocation improvement. Claude summarizes:

The lazy-frames change (your commit `0cb19469e2`) gives only a small speedup on ChEMBL: about 1.5–2.5% less CPU time for Klekota-Roth. Allocation drops by about 20%, and every fingerprint is identical to before.

I ran four streaming runs, each over 100,000 molecules (two disjoint ChEMBL batches, base and new). Each run covered all 100,000 with no failures. The checksums of every fingerprint matched for all four fingerprint types, in both batches.

| Fingerprinter | CPU time, batch A | CPU time, batch B | Allocation |
|---|---|---|---|
| Klekota-Roth | 1989 s → 1939 s (−2.5%, 95% CI −3.6% to −1.4%) | 1990 s → 1959 s (−1.5%, 95% CI −2.7% to −0.3%) | −19.5% (about 1.3 TB → 1.04 TB) |
| Functional-group | −2.0% (95% CI −3.6% to −0.4%) | −1.2% (95% CI −2.3% to −0.1%) | −9.7% |
| MACCS | 0.0% (95% CI −2.5% to +2.5%) | +0.9% (95% CI −1.4% to +3.2%) | −11% |
| 14 raw SMARTS | −1.8% (95% CI −4.9% to +1.3%) | +1.3% (95% CI −0.8% to +3.4%) | −0.9% |

- **Klekota-Roth:** the speedup is consistent in both batches, but small. A pass over 100,000 molecules takes about 33 minutes of CPU time, and the change saves 30–50 seconds of that.
- **MACCS and raw SMARTS:** the difference is within noise (the sign flips between batches).
- **Why the earlier 1000-molecule results looked worse:** the 10–24% slowdowns for "new" were noise from the shared machine, as I suspected. The 100k runs rule them out.
- **Why the gain is small:** the allocated stack frames were cheap. The JIT's escape analysis and the young-generation GC absorb most of that cost. Reducing allocation by 20% saves little time here.

The remaining cost is as the profile showed: `Expr.matches` (about 64%) and the per-atom and per-bond iteration. Changes 2–4 in my plan target that directly, in particular the first-atom prefilter. Should I start with change 3, the prefilter? It targets the biggest cost and should give a much larger gain than change 2, which only removes iterator allocations. Before I change anything, I'd record a JFR profile of the new build on ChEMBL to check that the hot spots match what I saw on MLProbes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8de9f35e3718`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.