# Issue

**Title:** feat(doping): add random concentration-based substitution mode

## Description

## Summary

Adds a **Random** mode to the interactive Doping pane, alongside the existing **Combinatorial** mode. It expresses *random, concentration-based* substitution — e.g. for MoS₂ (25 Mo + 50 S), **randomly replace 8 of the 25 Mo with 5 Nb + 3 Ta** at random positions — which the combinatorial product path can't do (`by_element` replaces *all* matching atoms; `by_indices` needs hand-picked sites).

## UI (`src/lib/structure/DopingPane.svelte`)

A top-of-pane toggle switches between **Combinatorial** (unchanged) and **Random**:

- **Host pool** — by element (with a live atom count) or by a captured 3D-viewer selection.
- **Dopants** — added from the periodic table; each amount set **by count** *or* **by percent** of the pool. The two columns stay in sync and re-derive when the pool size changes (e.g. host element switched).
- **Samples** — generate **N** independent random arrangements (default 10), optional **dedup**, optional **seed** for reproducibility.
- Results reuse the existing **Open as Trajectory** flow.

The inline and external periodic tables both route element clicks to the active mode, so no separate PT wiring is needed.

## Backend (`server/catgo/routers/build.py`)

New `POST /build/random-substitution`:

- `RandomSubstitutionRequest` / `RandomDopantModel` (element + count).
- Resolves the candidate pool from `host_element` **or** explicit `target_indices`.
- Validates `Σ count ≤ pool size`; assigns each dopant to distinct random sites with a seeded `random.Random`.
- Draws unique arrangements when `deduplicate` is set (capped attempts so a tiny pool can't spin), returns the existing `BuildResult`.

## API (`src/lib/api/build.ts`)

`random_substitution()` + `RandomSubstitutionParams` / `RandomDopant` types.

## i18n

`en/structure.ts` + `zh/structure.ts` strings for the new mode.

## Testing

- Backend functional test (MoS₂, host=Mo, Nb×5 + Ta×3, seed=42): output composition is exactly `{Nb:5, Ta:3, Mo:17, S:50}`; same seed is reproducible; 10/10 arrangements unique under dedup; over-pool request is rejected (HTTP 400); `target_indices` pool path verified.
- `svelte-check`: 0 errors (changed files clean).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5d87b6771691`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.