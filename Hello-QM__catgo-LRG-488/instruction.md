# Issue

**Title:** feat(viewer): selectable polyhedra render styles (flat/matte/glass)

## Description

## What

The frosted-glass polyhedra face look (merged in #486) is opinionated, so it's now **one of three selectable modes** (`polyhedra_style`), not the only rendering:

| Mode | Look |
| --- | --- |
| `flat` (**default**) | classic hard facets + headlamp lambert, raw element colour — the pre-#486 look |
| `matte` | smooth radial normals, soft diffuse, raw colour — middle ground |
| `glass` | frosted white-lifted tint + Fresnel rim glow + specular sheen (#486 look) |

One `u_style` int uniform branches the single face fragment shader (flat recomputes facet normals from screen-space derivatives); geometry unchanged. Style select lives in Controls → Polyhedra; i18n en/zh in parity. Fat `LineSegments2` edges + width slider stay shared across all modes. `polyhedra_edge_color` default reverted to dark `#333333` to suit the flat default (no auto-linkage with style — it would fight persisted settings; existing localStorage keeps the old colour until a section Reset).

## Verification
- `pnpm check` 0 errors; vitest 4436 passed (incl. new `tests/vitest/structure/polyhedra-style.test.ts`)
- Live on TiO₂ rutile: three modes screenshot pixel-diff distinct; UI select repaints immediately; flat matches the pre-#486 look

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2056e8e72b6b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.