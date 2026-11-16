# Issue

**Title:** Only write gfnff_topo when restart is enabled

## Description

> AI Disclaimer: The text in this description was written with the assistance of AI. The contents of the code change come from my own fork of xtb, and my own attempts to circumvent some unwanted file-writing behavior in GFN-FF a year ago.

`gfnff_setup` only reads `gfnff_topo` when `restart` is true, but it writes the file unconditionally. The C API always passes `restart = .false.`, so `xtb_loadGFNFF` writes `gfnff_topo` into the caller's working directory, and the file is never used. This PR applies the same `restart` guard to the write.

The command-line program is unaffected by default, because it passes `restart = .true.`. With `--norestart`, the file is no longer written, which matches the fact that it was never read in that case.

Partially addresses #1321.

Possible future work: GFN-FF also reads `charges` and `.CHRG` files from the working directory, including through the C API. In my tests, a stray file changed the GFN-FF energy with no warning. The `xtb` program itself writes `charges` after GFN1/GFN2 runs. Restricting these reads to the command-line program (similar to how #1438 passes the verbosity) may be worth exploring later.

<details>
<summary>Test: stray charge files change the GFN-FF energy (C API, upstream <code>main</code>)</summary>

One GFN-FF singlepoint through the C API (`xtb_loadGFNFF` + `xtb_singlepoint`, neutral system) on two water molecules 6 Å apart. Each run used a fresh, empty working directory. The decoy files assign +1/−1 to the two waters, so the total charge (0) still matches and xtb accepts them.

| Run | Energy (Eh) | Files in directory afterwards |
|---|---|---|
| clean, muted | −0.6541811687 | `gfnff_topo` |
| decoy `charges` file | **−0.1380080226** | `charges`, `gfnff_topo` |
| decoy `.CHRG` file | **−0.1380080226** | `.CHRG`, `gfnff_topo` |
| clean, full verbosity | −0.6541811687 | `gfnff_charges`, `gfnff_topo` |

Decoy files used:

- `charges`: six lines: `0.333333` (×3), then `-0.333333` (×3)
- `.CHRG`: two lines: `0`, then `1 -1`

With the two file reads disabled, all four runs give −0.6541811687 Eh.

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `33fe381adde7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.