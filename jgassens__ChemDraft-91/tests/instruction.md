# Issue

**Title:** Typing a label over a bond labels its nearer atom instead of switching tools

## Description

## Summary

This is the other half of the Eraser data-loss report (#84 fixed the Eraser's whole-molecule drag).

**The problem.** On a zigzag chain the pointer easily rests on a **bond** rather than an atom. Over a bond, every letter fell through to tool shortcuts, so typing `OMe` switched to the Single Bond tool on `m` and to the Eraser on `e`. Hover typing (#77) only worked while an atom was hovered. A drift off that atom onto its own bond ended the label mid-word.

**The change**, in the ChemDraft key scheme (the ChemDraw scheme is unchanged). Over a hovered bond:
- **Element key** (`O`, `N`, `C`, `S`, `F`, …): labels the bond's **end nearer the pointer**, exactly as if that atom were hovered, and opens the same label continuation.
- **A label in progress on one of this atom's own bonds:** every following letter and digit goes to that atom's label, so `CF3` keeps its `3` instead of setting a bond order.
- **Unchanged**, as over an atom:
  - a digit with no label in progress sets the bond order;
  - a non-element letter (`e`, `m`, …) runs its tool shortcut.

Leaving the labelled atom for one of its own bonds no longer ends the continuation. Moving on to a different atom still does.

## Files changed

- `apps/desktop/src/MainWindow.tsx`:
  - `hoverPagePointRef` (the last hover point);
  - `hoverLabelAtomTargetForKey` (which atom a key over a bond belongs to);
  - `hoverTargetKeepsLabelContinuation` (a drift onto the labelled atom's own bond keeps the label);
  - the keydown handler retargets the hover to that atom before the existing atom path runs;
  - the hover returns to the pointer target when the label ends; a layout effect ends the continuation on any tool change; `rederiveNativeCanvasHoverFromLastPointer` guards `elementFromPoint` (no such function in jsdom);
  - `CURRENT_BUILD_STAMP` is now `10.10.20.20-opus` (main merged at a4c8276).
- `apps/desktop/src/hoverLabelTyping.dom.test.ts`: five new DOM tests:
  - `OMe` over a bond labels the nearer atom;
  - the end nearer the pointer is chosen;
  - a drift onto the atom's own bond keeps the label;
  - a digit stays in the label mid-continuation;
  - a bare `e` and a digit over a bond keep their old behaviour.

  The first four fail on the previous code. Review follow-ups (acd26ba) add three more DOM tests (Delete after a committed label, and after a non-continuing key, hits the bond; a menu tool change ends the continuation), all failing before the fix, and unit tests for an exact-midpoint tie and a zero-length bond.
- `apps/desktop/src/hoverLabelStress.dom.test.ts` (new): the stress test below; 24 trials in CI, more via `HOVER_STRESS_TRIALS`.
- `apps/desktop/src/userFeedbackStress.dom.test.ts`: scenario D (O, drift onto the atom’s own bond, M, e) recorded this bug: the label stopped at `O` and `e` armed the Eraser. It now asserts the fixed behaviour: the editor reads `OMe`, the tool stays on Bond, and nothing is deleted. Its `it.fails` twin is folded in.

## Stress test (gate 1)

`OMe` + Enter typed with the pointer on a bond, at seeded random points along random bonds of a 33-atom zigzag chain: the middle 40% of the bond, or its midpoint if that point resolves to an atom. **Every trial is asserted to start over a bond.** Each trial undoes back to the plain chain. A trial counts as labelled only if exactly one atom changes, it reads `OMe`, and it is an end of that bond.

| 200 trials, all starting on a bond | labelled correctly | tool switched | structure changed |
|---|---|---|---|
| previous code (main a7fdd0b) | 0 | **200** | 0 |
| this branch (acd26ba) | **200** | **0** | 0 |

## Tests run (Windows 11)

- `pnpm lint`: pass.
- `git diff --check`: pass.
- `vitest` on `hoverLabelTyping`, `atomLabelEditFocus`, `hoverLabelStress`, `keyboardShortcuts`, `App.test.ts` and `eraserMolecule`: **316 passed**.
- Full suite (`pnpm vitest run`, 3e30e4e): **275 files, 5,311 tests passed, 0 failed** (33 skipped).
- After merging main (a4c8276, #89): lint, `git diff --check`, and focused vitest on this change's suites plus #89's sketch tests: **11 files, 350 passed**.
- No Rust changes.

## Platforms

- **Windows:** verified in jsdom, as above, and in a launched release build of 3e30e4e with trusted CDP pointer and key input, the Chain tool active, on a 34-atom chain:
  - step 1 below passed 69 of 70 trials over seven launches, plus 40 of 40 at seeded random spots;
  - steps 2 and 3 passed 7 of 7 each;
  - no uncaught exceptions.

  The one failure was the first trial after the first launch of the build. `O` labelled the hovered atom, but the label did not continue, so `M` and `e` ran tool shortcuts. It went through the existing atom path.

  It was not reproduced as an app fault in ten cold first launches with fresh app data, typing at keyboard pace from about 1 s after the window was ready, with per-key traces:
  - 97 of 100 trials passed, and nine of the ten launches passed 10 of 10.
  - The three failures, all in one launch, show pointer events my injected input never sent. The pointer crossed `bond_015` and `atom_016` and left the hovered atom with no injected move. That is the physical mouse moving over the window and overriding the test pointer.
  - With the hover gone, `O` and `M` fell through to shortcuts and `e` chose the Eraser. In one trial, `O` relabelled the previous trial's atom, which was still selected. That is existing selected-atom behaviour.
  - The first-launch failure fits the same interference but can't be proven: seen once in 70 step-1 trials, not reproduced.
- **macOS: unverified.** The change is shared TypeScript with no platform branch, so the Mac step below is the owner's.

## For the owner: hands-on check

1. Draw a long chain with the Chain tool. Rest the pointer on a **bond** (not an atom) and type `OMe`, then Enter. The atom at the end of that bond nearer the pointer becomes OMe, and the tool doesn't change.
2. Hover an atom and type `O`, then nudge the pointer a little onto one of that atom's bonds, short of the bond's middle. Type `Me` and Enter. The label reads OMe.
3. With the pointer on a bond, press `2` (the bond becomes double), then press `e` (the Eraser is chosen, as before).

## Known limitations

- **Tool shortcuts still fire:** a non-element letter typed over a bond with no label in progress still switches tools (`e` → Eraser), the same as over an atom. Only label typing is captured.
- **ChemDraw scheme unchanged:** its bond-letter hotkeys are untouched.
- **A drift onto the neighbouring atom still ends the label:**
  - On a chain bond (22 page px at 100% zoom), the bond's hover zone is only 40–60% along it. The rest belongs to its two end atoms.
  - Moving onto a different atom ends the label, as before this change. So a nudge past the middle, onto the next atom, sends `M` and `e` to tool shortcuts.
  - This is #77's design, left unchanged here.

## Review

## One recommended next task

None from this change.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `faa3124e285a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.