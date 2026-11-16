# Issue

**Title:** fix: charge/COHP remote import + cube periodicity + slice-plane UX

## Description

Batch of live-found fixes from v1.3.2 field testing (held back from the release; targets a future v1.3.3).

## Charge analysis — Browse Remote
- **Browse Remote did nothing.** `FileSourceDialog` was gated internally on `{#if show}`, but `ChargeAnalysisPane` never passed `show`. Now always-mounted with `bind:show` (matches the working `DosAnalysisPane` pattern; no `{#if}` wrapper).
- **Remote download 405 "Method Not Allowed".** Frontend POSTed to a nonexistent `/api/chgcar/download`, which fell through to the SPA catch-all `GET /{full_path:path}` → 405. Now routes remote CHGCAR/Bader through the existing `GET /api/hpc/download` (`getDownloadUrl`).

## COHP — remote ICOHPLIST
- Support importing `ICOHPLIST` from a remote HPC session (terminal / Browse Remote), matching the other electronic panes.

## Cube periodicity
- A loaded CHGCAR/CHGDIFF density showed **no cell** (rendered as a molecule). Now derive the lattice from the cube grid for VASP-origin densities (`CHGCAR`/`CHGDIFF`/`AECCAR`/`LOCPOT`/`ELFCAR`/`PARCHG`/`*.vasp`) so the slab renders with its unit-cell box + PBC bonds. Genuine molecular Gaussian cubes stay non-periodic (their grid is a padded bounding box).
- Threaded the `{ periodic }` flag through **all three** cube-load paths: `Structure.svelte`, standalone desktop `App.svelte`, and the VS Code webview.

## Cube slice plane UX
- **3-Atom mode did nothing** when a selected atom was a PBC image (displayed index ≥ base atom count). Now resolves positions/elements via `display_positions`/`display_elements`, so image atoms are valid plane anchors.
- Replaced the Position/Offset/Tilt **sliders with up/down stepper buttons** on `x`/`y`/`z` and `3-Atom` modes (per request — precise keyboard-free nudging; sliders were imprecise and native spinners don't render in WebKitGTK).
- 2D slice figure **auto-crops to the atom region** (new "Fit" toggle, default on) so the slab fills the frame instead of being lost in vacuum; added a **human-readable orientation hint** (e.g. `horizontal ≈±x · vertical ≈±z · z = depth`).

## Tests
- `tests/vitest/cube/periodic-cube-lattice.test.ts` (5 tests) — cube-grid → lattice derivation, periodic vs non-periodic.

i18n en/zh kept in parity.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2fd9a6794b33`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.