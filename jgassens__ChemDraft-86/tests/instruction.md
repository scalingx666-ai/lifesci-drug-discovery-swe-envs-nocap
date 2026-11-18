# Issue

**Title:** Chain and arrow drags that start on an object follow the pointer

## Description

## Summary

**Dragging a chain off an existing atom added one carbon and stopped.** The Windows session found this on #81 (on `main` too). Pressing a ring atom or a chain's end atom with the Chain or Flexible Chain tool placed one carbon on press, and the chain never grew as the pointer moved. **The same cause also broke arrows drawn starting on top of a molecule:** reaction arrows and art arrows landed at their default length instead of following the drag. The comment at that branch says arrows commonly start on a reagent.

**Cause** (diagnosis by the Windows session, confirmed here):
- `startNativePlacementDrag` captures the pointer on `event.currentTarget`. For a press that starts on an object, that is the object's element (`MainWindow.tsx`: the anchored chain, reaction arrow and art-line branches of `handleObjectPointerDown`).
- With capture on the object, the browser delivers every later move and the release to the object's handlers.
- `handleObjectPointerMove` calls `stopPropagation()` first and had no placement-drag branch. Only `handlePagePointerMove` / `Up` / `Cancel` knew about placement drags, so the preview never ran, and the release committed what the press placed.

**Fix:**
- The placement drag's move and release are now two shared callbacks, `continueNativePlacementDrag` and `finishNativePlacementDrag`.
- The page handlers call them (their code moved there unchanged), and so do the object handlers.
- `handleObjectPointerCancel` gained the same inline restore as `handlePagePointerCancel`: reset the state machine, restore the start document, clear the drag. It is kept inline because `pointerCancelCoverage.test.ts` requires each cancel branch to show its disposal in the handler body. A shared abandon helper in the first commit hid it from that scan, and `0d22375` fixes that.
- The object branches match on the pointer id only, because the press may have been re-targeted to another molecule's wrapper.
- The agent bridge, which delivers moves to the pressed object's `[data-object-id]` element, takes the same path.
- Every other drag that starts on an object (part drags, rotate, resize, the bond tool's drag off an atom) already had its branch in the object handlers. Placement drags were the one kind missing.

## Tests

`apps/desktop/src/placementDragCapture.dom.test.ts` (new, jsdom) renders `MainWindow` and drives the real handlers. It stubs pointer capture on `Element.prototype`, then **delivers every move and the release to whichever element captured the pointer**, as a browser does. Six of them fail on the previous code, where the chain stays at press + 1 carbon and arrows stay at 160 / 120 px:

- a chain dragged off a benzene ring atom: the preview grows mid-drag, one bond per added atom, the commit derives the SMILES, and one undo removes the whole gesture;
- a chain dragged off a chain's end atom: SMILES = n × `C`;
- a flexible chain dragged off a ring atom, around a corner;
- an art reaction arrow and a legacy reaction arrow, each started on top of a molecule, both stretch with a 300 px drag;
- `pointercancel` delivered to the capturing object restores the molecule; Escape mid-drag followed by the release commits nothing.

After #77 (`aa9c028`), two more cases: a chain dragged off an atom with Alt held commits the free aim, and without Alt it commits the 15° grid. Each equals `applyNativeChainTool` with the same anchor and `placementAltKey`, and the release carries the opposite modifier. The Alt case fails without the ported line.

Why tests missed it: the existing anchored-chain DOM test (`graphicPathEdit.dom.test.ts`, "commits a dragged chain…") pressed on the molecule but sent its moves to the page element. No browser does that once an object has captured the pointer. That test still passes, because the page path is unchanged.

## Platforms

- **Catch-up with #77 (`aa9c028`):** a merge of `origin/main`, with no rewrite. There were three conflicts, all in `MainWindow.tsx`:
  - the stamp, set to a fresh `10.10.17.21-opus`;
  - the page pointermove branch: kept the shared helper, and moved #77's `altKey = event.altKey` into `continueNativePlacementDrag`, so Alt reaches drags captured on an object;
  - the page pointerup branch: kept `finishNativePlacementDrag`, which already passes the release point (or the latest point); #77's `commitNativePlacementDrag` uses the release point only for arrows.

  Results: `pnpm lint` ✅; all of `apps/desktop` in the heavy slot ✅ (152 files, 2584 passed, 1 skipped), which covers the DOM, agent-bridge and drawing-tool suites, `pointerCancelCoverage`, and #77's `placementSnap`, `hoverLabelTyping`, `userFeedbackStress`, `ringPress` and `atomLabelEditFocus`; `git diff --check` ✅.
- **Windows, in the app:** the Windows session's trusted-CDP pass on `0d22375`, all 5 steps passing (details in its comment):
  - the Chain tool off a benzene atom grows +60 C across the page corner;
  - the Flexible tool off a benzene atom grows +200 C at a flat 57–69 ms/move at 50/100/150 C;
  - off a chain end: 5 → 36 atoms;
  - flexible around a corner: 6 → 31 atoms;
  - an art arrow and a reaction arrow pressed on a ring atom both stretch to 340 px;
  - Escape mid-drag commits nothing.
- **Windows, gauntlet:** `pnpm lint` ✅; full `pnpm vitest run` on `0d22375` in the heavy slot ✅ 4424 passed, 0 failed (incl. the DOM, agent-bridge and drawing-tool suites and `pointerCancelCoverage`); `git diff --check` ✅. CI on `0d22375`: all 4 checks ✅ (clippy `-D warnings` and `cargo test` on macOS and Windows; no Rust changed since `f662fe5`).
- **macOS:** not verified; same steps as the owner check.

## Gates

- [x] Stress test: the §14 gauntlet; DOM, agent-bridge and drawing-tool suites; and the Windows in-app trusted-input pass on `0d22375`
- [ ] Owner hands-on check on a launched build
- [x] Review: claude-fable `fable-pr86-20261010` (f662fe5..0d22375) APPROVE, no findings. The arrows stay in scope; a second simultaneous pointer overwriting the drag ref is pre-existing and was declined.
- [ ] macOS check

## Squash-merge message

```
Chain and arrow drags that start on an object follow the pointer

Dragging a chain off an existing atom added one carbon and never grew,
and an arrow drawn starting on top of a molecule landed at its default
length. A press on an object captures the pointer there, so every later
move and the release reach the object's handlers, which had no
placement-drag branch. The placement drag's move and release are now
shared by the page and object handlers, and both cancel handlers restore
it inline. The shared move reads Alt, so a chain dragged off an atom
takes the free aim with Alt held, as one started on the page does.

```

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7a0c0ecc2195`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.