# Issue

**Title:** feat(workflow): adsorbate-only freeze for frequency calcs (C1)

## Description

First slice (C1) of the **workflow freeze correctness** effort — spec at `docs/superpowers/specs/2026-06-23-workflow-freeze-correctness-design.md`.

## Why

Frequency calcs on adsorbate/slab systems must **fix the entire slab and vibrate only the adsorbate** (harmonic-adsorbate approximation). Today freq nodes default to bottom-N-layer freezing (same as geo_opt), so top slab layers get vibrated — physically wrong ZPE/entropy. The enabler bug: adsorbate atoms aren't identifiable downstream (`adsorbate_placement.py` computes the indices but `run_adsorbate_place` discards them).

## What

1. **Tag adsorbate atoms** — `run_adsorbate_place` writes an `is_adsorbate` site property (True on adsorbate, False on slab) in both the ferrox and pymatgen-fallback paths.
2. **New `freeze_mode: adsorbate`** (backend `vasp.py` freq block + frontend `freeze.ts`) — fixes every non-tagged atom, frees only the adsorbate; warns + freezes nothing when no tag is present (no silent mis-freeze).
3. **freq node defaults to `adsorbate`** + editor quick-button "Fix slab, vibrate adsorbate only" (en/zh i18n).

## Verification

- `test_adsorbate_tagging.py`, `test_freq_adsorbate_freeze.py` (incl. no-tag fallback), `freeze.test.ts` (+2 adsorbate cases) — **all pass**.
- End-to-end on the real ORR slab params: slab(36) → adsorbate → freq POSCAR = **36 slab atoms `F F F`, 3 OOH atoms `T T T`**.
- i18n en/zh parity test passes.

## Follow-ups (separate PRs, per spec)

- C2: CatBot generation freeze defaults (quickbuild `vasp_freq` → adsorbate, etc.)
- C3: param/freeze validation (warn-mostly, block freeze-layers > slab-layers)
- C4: post-generation "review the workflow" reminder

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `24ee86fcb8b4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.