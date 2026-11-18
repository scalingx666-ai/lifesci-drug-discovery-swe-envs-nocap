# Issue

**Title:** chemdraft nmr: drop NMR plugin workarounds; require a current plugin

## Description

The NMR predictor plugin now fixes the two bugs the CLI was compensating for (jgassens/ChemDraft-NMR-Plugin main, 119001c):

- **Equivalence grouping.** Topologically equivalent atoms are one resonance with `nEquivalent` counting them (toluene 13C: 5 resonances, was 6). Stereochemically distinct members of a merged group are disclosed with `NMR_POTENTIALLY_DIASTEREOTOPIC_HYDROGENS` / `_METHYLS` / `NMR_STEREO_NONEQUIVALENT_MERGED`; no shift is fabricated.
- **Spectrum caption.** Says "synthetic fixture" only for fixture results; real predictions say "predicted".

This PR:

1. Removes the caption relabel (`NMR_SPECTRUM_CAPTION_UNVERIFIED`) and the equivalence-split check (`NMR_EQUIVALENCE_SPLIT` / `NMR_EQUIVALENCE_UNCHECKED`, the `equivalence-split` flag). The stick-height note on the figure stays.
2. Corrects the help text and README on how grouping works.
3. Guards against old plugin checkouts: `loadNmrPlugin` requires the plugin's `NMR_PLUGIN_CAPABILITIES` to include `constitutional-equivalence-grouping`, `diastereotopic-disclosure` and `truthful-spectrum-caption`. Otherwise the command fails with what is missing and how to update. Without this, an old checkout would pass split resonances and a fixture caption through silently.

## Testing
- `npx vitest run packages/chemdraft-cli`: 151 passed, run against the pushed plugin `main`.
- `pnpm chemdraft nmr --smiles Cc1ccccc1 --nuclei 13C`: 5 resonances, caption "δ (ppm) — predicted".
- `pnpm chemdraft nmr --smiles 'C[C@@H](O)C(C)C'`: diastereotopic-methyl warning present.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c7d404bf133a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.