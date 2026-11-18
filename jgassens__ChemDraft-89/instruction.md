# Issue

**Title:** Sketched hash ticks and dashes get a hand-drawn jitter

## Description

## Summary

With the sketch effect on, #77 made hashed and dashed bonds draw as separate rough strokes instead of a spine with ticks. The owner found those ticks too regular: "the dashes seem to lack the whimsy of the other lines". This PR gives each hash tick and each dash a seeded, hand-drawn jitter that matches the plain sketched bonds:

- a tilt of up to ±14° (at roughness 1.25);
- length varying by up to ±25%;
- stroke weight varying by up to ±40%;
- a small sideways shift along the bond;
- a slight bow in each mark.

The jitter scales with the sketch's `roughness` and saturates at twice that strength from roughness 2.5 up (tilt up to ±28°). The `seed` fixes it, so re-renders match.

Each mark is fitted as a whole, so a hashed bond still widens from its narrow end, and neighbouring ticks never touch or cross. In cramped cells only that one tick's tilt is reduced. The canvas and every export share one plan, so they draw the same marks. Chemistry is untouched: this is drawing only.

## Files changed

- `packages/layout-engine/src/sketchTicks.ts` (new): `moleculeSketchTickPath`, the per-mark jitter
- `packages/layout-engine/src/formatNumber.ts` (new): the one SVG number formatter, shared by `index.ts` and `sketchTicks.ts`
- `packages/layout-engine/src/index.ts`: sketch base path uses it for hash ticks and dashes
- `packages/art-engine/src/index.ts`: an optional `sketchLineOverrides` hook that lets the caller replace single straight edges of the sketch path with its own rough marks; the geometry stays in layout-engine
- Tests: `layout-engine/src/{sketchTicks,sketchTickGeometry,sketchStereoBonds}.test.ts`, `sketchRegression.fixture.ts`, `art-engine/src/sketchLineOverrides.test.ts`, `export-engine/src/sketchTicks.test.ts`
- `apps/desktop/src/MainWindow.tsx`: build stamp `10.10.18.50-codex`

## Tests

On macOS, at `3334bda7` (and lint plus the layout-engine, art-engine and export-engine tests again at `98291198`: 526 passed):

- `pnpm lint`: pass
- `pnpm vitest run`: 5338 passed, 13 skipped (284 files)
- `pnpm build`: pass
- `git diff --check`: clean
- No Rust changes.

## Stress test

The stress test is posted as a comment. Summary: 9 PubChem molecules with heavy stereochemistry, every third non-ring single bond made dashed, and the sketch at 3 settings. All 27 renders keep the canonical SMILES and stereocentre counts of the unsketched render, and none has NaN in its SVG.

## Gates

- [x] Stress test (comment below)
- [x] Review: Kimi found it ready at `3334bda7`; three follow-ups fixed in `98291198`, re-reviewed by Fable (ready)
- [ ] Owner hands-on check: on a packaged build, the master pre-tests first

## Platforms

- **macOS:** tests, build and renders checked.
- **Windows:** CI only; appearance on Windows not checked by hand. The code is shared TypeScript with no platform branch.

## Known limitations

- A mark in a very cramped cell is drawn with almost no tilt, so neighbouring ticks stay separate.
- On a bond shorter than about one stroke width, hash tick centres can coincide.

## Review

- `kimi-k3 kimi-dashes-review-20261010` (whole change, `a7fdd0b1..3334bda7`: ready)
- `claude-fable fable-dashes-rereview-20261010` (fixes `3334bda7..98291198`: ready)
- `claude-fable fable-zero-test-review-20261010` (test tightened in `273f69f5`: fails on the pre-fix code, passes on the fix; ready)

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a7fdd0b127cb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.