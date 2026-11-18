# Issue

**Title:** Eraser drags erase only what they touch on a molecule

## Description

## Summary

An Eraser **drag** deleted every molecule it touched, whole. A short sweep across two or three bonds of a forty-carbon chain removed the entire chain. The owner hit this while testing #77: a hovered bond turned typed letters into tool shortcuts, `e` picked the Eraser, and the next drag took the chain.

Now an Eraser drag over a native molecule erases **only what it touches**: the atoms inside the rectangle and the bonds it crosses. It goes through the same part-delete path Delete uses for a partial lasso selection (`applyNativeMoleculePartDeleteTarget`), as one undo entry.
- Shapes, text and other objects the drag touches are still removed whole, as before.
- A molecule the sweep encloses completely is still removed.
- A molecule the part-delete path refuses (not an editable native graph) is removed whole, as the Eraser always did.

**Atoms a sweep leaves with no bonds.**
- A bare skeleton carbon (C, uncharged, no radical, no typed or visible label) is removed too; otherwise it would render as a stray "CH4".
- A labelled, charged or radical atom (O, N, Cl, C+ …) stays as a visible fragment, because erasing it would change chemistry the user didn't touch (AGENTS.md §7).
- Atoms that had no bonds before the sweep are never touched.

**Live preview.** While the drag is in progress, the touched atoms and bonds turn red and objects that will go whole get an outline. The preview comes from the same `eraserSweepInSelectionRect` the release applies, so what is highlighted is exactly what gets erased. Leftover selection highlighting, such as a chain the chain tool just selected, is hidden during the sweep so it can't suggest a bigger erase (owner finding on the Mac build of 80fab69).

The status line now says what went: "Erased 3 bonds", "Erased 1 bond, 1 object", "Nothing erased".

## Files changed

- `apps/desktop/src/MainWindow.tsx`
  - `eraserObjectIdsInSelectionRect` becomes `eraserSweepInSelectionRect`, which returns whole objects and molecule parts separately.
  - New `eraserSweepMoleculePart` (the stranded-atom rule), `applyEraserSweep` (one document change) and `eraserSweepStatus`.
  - The Eraser marquee's pointer-up handler uses them.
  - `CURRENT_BUILD_STAMP` is now `10.10.13.20-opus`.
- `apps/desktop/src/MainWindow.tsx` (553b8ac): `eraserSweepPreview` state, recomputed on each marquee move; `EraserSweepPreviewOverlay`; selection chrome is off during the sweep. `App.css`: `.eraser-sweep-object`.
- `apps/desktop/src/App.test.ts`: the existing shape/text test is moved to the new function, plus six new tests:
  - partial chain;
  - ring-fusion bond;
  - text lying on a molecule;
  - bare vs labelled stranded atom;
  - full enclosure;
  - shape and molecule in one sweep.
- `apps/desktop/src/eraserMolecule.dom.test.ts` (new): drives the real pointer handlers in jsdom.
  - A thin vertical sweep across a 30-bond chain removes one bond. The status line reads exactly "Erased 1 bond". `edit.undo` restores it and `edit.redo` repeats it.
  - A sweep around the whole chain removes it as one undo step, with status "Erased N atoms, M bonds".
- Review follow-ups (80fab69):
  - an atom fully inside the sweep is erased with both of its bonds;
  - a wedge, a formal charge and a ring fill on the remaining parts survive;
  - the status text is asserted exactly, read from the main window's `role="status"` region;
  - stamp `10.10.12.25-opus`.
- Preview DOM tests (553b8ac): the highlighted atoms, bonds and objects during the drag equal what release removes, for a partial sweep, a whole-molecule sweep and a sweep through a bond plus a text box. The leftover selection is shown before the drag and hidden during it. Stamp `10.10.13.20-opus`.

## Tests run (Windows 11, after merging `main` 65e882a)

- `pnpm lint`: pass
- `pnpm vitest run`: **250 files, 4416 tests passed**, 0 failed. This was run on an idle machine; under four concurrent sessions, `joback.real.test.ts` and a `toolsetBridge` stress route time out at 5 s on clean `main` too.
- `pnpm build`: pass
- `git diff --check`: pass
- `cargo fmt --check`, `cargo clippy --all-targets -- -D warnings`, `cargo test` (207 passed): pass. There are no Rust changes.

## Platforms

- **Windows:** the logic and pointer handling are verified by the tests above, run on Windows. A hands-on pass in the launched app is pending (owner check below).
- **macOS: unverified.** The change is pure TypeScript with no platform branches, but it still needs a launched Mac build and the same hands-on check.

## For the owner: hands-on check

On a launched build of this branch:
1. Draw a long chain. Choose the Eraser and drag a small box across two or three bonds in the middle. Only those bonds go; the rest of the chain stays, now in two pieces. Ctrl+Z brings the bonds back, and Ctrl+Y erases them again.
2. Draw a short chain and label its end `OH`. Drag the Eraser across the C–O bond only. The bond goes and the O stays as its own fragment.
3. Drag the Eraser around an entire molecule. It disappears.
4. Drag one sweep across a text box or shape and a molecule. The text or shape goes whole, and only the touched part of the molecule goes.

## Known limitations

- **Click vs drag, labelled end atoms:** an Eraser *click* on a terminal bond (unchanged `deleteNativeCarbonBond`) still removes the dangling end atom whatever its label, while a *drag* keeps a labelled end atom. Accepted by the coordinator for now; step 2 above lets the owner see it.
- **Click vs drag, stranded neighbours:** a box drawn around a single atom also removes the bare-carbon neighbours it strands, so a box around one atom of ethane removes the whole molecule. A click on that atom (`deleteNativeCarbonAtom`) doesn't. Behaviour kept on purpose, per review.
- **Pre-existing marquee gap:** switching tools by shortcut in the middle of an Eraser drag leaves the preview up until the next pointer move, and the release then selects instead of erasing. Marquees have no Escape or blur cancel; this PR doesn't change that.
- **Pre-existing, not changed here:** mechanism arrows and electron marks anchored to an atom that gets erased stay in the document and stop rendering. Delete and the Eraser click behave the same way.
- **Bond-hover letters:** letters typed while hovering a bond still fall through to tool shortcuts (`m` → bond, `e` → Eraser). That half of the bug is deferred until #77 (hover typing) merges, to avoid conflicting with its hover-key design.
- **Speed on long chains:** each erase on a long acyclic chain re-derives SMILES through `longestNativePath`, which costs about 1–2 s per erase at 200 atoms on `main`. #81 fixes that path.

## Review

## One recommended next task

Once #77 merges, stop plain letters from switching tools while an atom or bond is hovered (the other half of this bug).

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `caa7c6c986f5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.