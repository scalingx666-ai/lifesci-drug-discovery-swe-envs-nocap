# Issue

**Title:** CLI PDF export places centred labels where the drawing puts them

## Description

PDF export through the `chemdraft` CLI (and so the MCP tools) misplaced centred text, a pre-existing bug. Sodium benzoate came out as `Na  O  +  ⁻O`: the centred Na and O labels sat about 40 px left of their atoms, and the start-anchored charges stayed put. Cause: the CLI's headless DOM made `SVGElement.getBBox()` return a fixed 80×16 box, and svg2pdf uses that width to resolve `text-anchor`. The in-app PDF export measures with the real browser and was never affected.

The CLI now measures text and tspans with the font svg2pdf actually draws them in. It follows svg2pdf 2.7.0's own font and style resolution: weight strings such as `500normal`, family-only changes that keep the current style, its fallback for unregistered styles, and tspan overrides measured before svg2pdf applies them. Kerning is off, matching the unkerned text jsPDF emits. The shim stays scoped and is restored after each export.

**Before → after (centre x, px; target = SVG position):** Na 339.2 → 369.7; O⁻ 363.5 → 397.7; carbonyl O 412.0 → 446.2; centred Arial text 179.8 → 200.0. Kerned "ToToTo" and weight-500/800 "MMMM" cases centre exactly at 100.

**Tests:** label positions read from the PDF by an independent glyph-width reader (not the helper under test), within 0.15 px: sodium benzoate; centred text; kerning; weights; inherited weight with a monospace family; mixed-font tspans on svg2pdf's ordinary and textLength paths; nested tspans. `pnpm lint` ✓; `packages/chemdraft-cli` + `packages/export-engine`: 396 tests ✓ (macOS). A sample rendered with this branch and #139's fonts matches the PDF sample the owner approved.

**Platforms:** CLI-only TypeScript; CI runs it on Windows. No app UI change.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `960678d71679`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.