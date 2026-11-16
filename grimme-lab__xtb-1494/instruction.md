# Issue

**Title:** fix cutoff for pi-bond and neighborlist in gfn-ff

## Description

This PR fixes two GFN-FF topology setup issues uncovered while benchmarking against GMTKN55:

- In-place neighbor deletion bug in `nbondmat_pbc` introduced in #929 between `6.6.1` and `6.7.1`) when generalizing `nbondmat` to `nbondmat_pbc`. Whenever an atom had two or more unpaired bonds, subsequent deletions overwrote previously shifted entries and left duplicate neighbors in `nbr`, corrupting topological distances (`bpair`) and bond/torsion assignments (up to `26.33 kcal/mol` error on `AL2X6/al2me6`).

- Numerical threshold for Hückel $\pi$-bond orders `pibo` were so far compared to 0 without a threshold leading to numerical noise changing the results. This becomes apparent after #1223 and #1474 fixed `fermismear` leaving floating-point roundoff from `DSYEV`.

When checking the remaining differences on the GMTKN55, the results are now again consistent with 6.6.1 except for actual fixes introduced before (e.g. `PX13/hf_2_ts` which had the wrong conjugation). Here, I also compare to the old `autoaa` Bohr-to-Ångström conversion factor replaced in #1478

| Structure | `6.6.1` (`Eh`) | `6.7.1` (`Eh`) | `HEAD` (`Eh`) | `This PR` (`Eh`) | `This PR (reverted autoaa)` (`Eh`) | $\Delta E$ (`This PR` vs `6.6.1`, `kcal/mol`) | $\Delta E$ (`reverted autoaa` vs `6.6.1`, `kcal/mol`) | Cause |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :--- |
| `AL2X6/al2me6` | `-3.391756408158` | `-3.349803223424` | `-3.349803224106` | `-3.391756408840` | `-3.391756408158` | `-0.0000004` | `0.0000000` | Fixed `nbondmat_pbc` (`#929` regression) |
| `MB16-43/27` | `-2.343738935971` | `-2.340350477480` | `-2.340350465271` | `-2.343738923763` | `-2.343738935960` | `+0.0000077` | `+0.0000000` | Fixed `nbondmat_pbc` (`#929` regression) |
| `ALK8/li_ch2n` | `-1.147379513201` | `-1.147071974902` | `-1.147071961746` | `-1.147379500045` | `-1.147379513201` | `+0.0000083` | `0.0000000` | Fixed `nbondmat_pbc` (`#929` regression) |
| `PX13/hf_2_ts` | `-0.215661964496` | `-0.215661964496` | `-0.242356224433` | `-0.242356224433` | `-0.242356225080` | `-16.7509010` | `-16.7509014` | Fixed `fermismear` (`#1223`/`#1474`) + `pibo` threshold |
| `PX13/hf_4_ts` | `NaN` | `NaN` | `-0.289737848872` | `-0.289737848872` | `-0.289737833772` | — | — | Fixed `qafac` overflow (`#1288`) |
| `PX13/hf_6_ts` | `NaN` | `NaN` | `-0.502995961673` | `-0.502995961673` | `-0.502995945285` | — | — | Fixed `qafac` overflow (`#1288`) |
| `RSE43/P43` | `SIGSEGV` | `-1.213125222154` | `-1.213125222895` | `-1.213125222895` | `-1.213125222154` | `-0.0000005` (vs `6.7.1`) | `0.0000000` (vs `6.7.1`) | Fixed special torsion (`#854`) |
| `C60ISO/10` | `-17.510384454502` | `-17.510384454502` | `-17.510384282608` | `-17.510384282608` | `-17.510384454502` | `+0.0001079` | `0.0000000` | `autoaa` conversion factor (`#1478`) |
| `DC13/c20cage` | `-5.460517681855` | `-5.460517681855` | `-5.460517536913` | `-5.460517536913` | `-5.460517681854` | `+0.0000910` | `+0.0000000` | `autoaa` conversion factor (`#1478`) |

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `156c0edf42c6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.