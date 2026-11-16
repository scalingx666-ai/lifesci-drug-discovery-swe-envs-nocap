# Issue

**Title:** fix(mobile): hide backend-only Analysis + Doping surfaces in STATIC_ONLY builds

## Description

Pre-submission audit of the iOS (`VITE_STATIC_ONLY=1`) build found two reviewer-reachable surfaces that hit the **"requires the CatGo desktop app" 503 / download-desktop prompt** — App Store **Guideline 2.1 (App Completeness)** rejection risks. Everything else (view/edit/parse structures, WASM bonds, offline builders, OPTIMADE/PubChem search, local optimizer) already works without a backend.

### Fixed
- **Analysis toolbar button** was ungated, unlike its workflow/server/chat/terminal neighbours — stayed live on mobile despite `MobileWorkspace` listing `'analysis'` in `HIDDEN_TOOLBAR`. Its DOS/band/COHP/freq/charge sub-tabs are backend-only (no WASM fallback) → 503 on tap. Now gated `!hidden_toolbar_items.includes('analysis') && !STATIC_ONLY`.
- **Doping build tab** — the only build sub-tab with no client-side path (combinatorial/random substitution → backend); it rendered `DesktopRequiredNotice` with the literal "download desktop / github.com" text. Hidden from `BuildPane`'s tab list on `STATIC_ONLY`, with a defensive guard on the `DopingPane` render in `Structure.svelte`.

Desktop (non-STATIC_ONLY) unchanged. `svelte-check` clean on the 3 files.

Source: background audit of `src/lib/mobile/` + every `STATIC_ONLY` gate.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8e9043164883`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.