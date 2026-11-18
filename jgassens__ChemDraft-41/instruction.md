# Issue

**Title:** Headless SMILES renderer (pnpm render) for exam and document images

## Description

## What

A command-line renderer, `packages/render-cli`, that turns a SMILES into SVG and PNG drawn the same way the app draws a pasted SMILES, with no app window:

```
pnpm render --smiles 'CC(=O)Oc1ccccc1C(=O)O' --out aspirin.png
pnpm render --batch jobs.json --out-dir structures/ --format both
```

It reuses the existing pieces unchanged: RDKit 2D layout with OpenChemLib as fallback, `insertSmilesMolecule` from the desktop, the export engine's SVG (cropped to the molecule), and `@resvg/resvg-js` for PNG. One JSON line per structure on stdout; a bad SMILES is reported, not thrown, and does not stop a batch.

## Why

An exam-writing Claude Code session cannot draw molecules. A `chem-structures` skill (in `~/.claude/skills`) now tells it to write the SMILES, run this command, and place the PNG in the document.

## Chemistry guards

- Radicals and isotopes are refused with `ok:false` (the paste path cannot represent them, so drawing would silently give the wrong molecule).
- `stereoCenters` counts specified centres; `unspecifiedStereoCenters` reports chiral centres left flat.
- Tests read R/S back out of the rendered molecule.

## Checks

- `pnpm lint` clean; full vitest suite 3336 passed.
- Build stamp bumped.
- Cross-reviewed by the Fable worker; all four findings fixed. Its vitest alias suggestion was rejected (breaks sub-path imports in the desktop).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a16d82fe1d19`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.