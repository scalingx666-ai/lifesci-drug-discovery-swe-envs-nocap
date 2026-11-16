# Issue

**Title:** fix(electronic): axis title no longer overlaps tick labels at large font

## Description

## Problem

Enlarging the axis-title font (标题字号, configurable up to ~30) in the electronic-structure plots made the axis title overlap / cover the tick labels behind it. Reported for DOS; the same bug affected Band and COHP plots.

## Cause

All three Plotly plots used a hard-coded layout `margin: { l: 60, r: 10, t: 10, b: 45 }` with no `automargin` or title `standoff`. The title font scaled with `title_size`, but the margin band stayed fixed, so a big title was drawn into the same 60px-left / 45px-bottom band as the tick labels.

## Fix

Add `automargin: true` to both axis objects in:
- `DosPlot.svelte` (energy_axis + dos_axis)
- `BandPlot.svelte` (xaxis + yaxis)
- `CohpPlot.svelte` (energy_axis + cohp_axis)

Plotly now expands the margin to fit ticks + title at any font size. No shared chart component exists, so the fix is applied per file.

## Test

User verified in the running desktop app: cranking 标题字号 to 30 no longer covers the tick labels. `pnpm check` introduces no new errors (the 9 pre-existing errors are in unrelated whisper test files).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f50b5cb249d5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.