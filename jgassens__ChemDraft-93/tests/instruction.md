# Issue

**Title:** A label in progress survives the pointer drifting off its atom

## Description

## Summary

Follows #91 (stacked on `claude/bond-hover-letters`; retarget to `main` once #91 merges).

**The problem.** A hover label ended as soon as the pointer left the atom being labelled. Typing `O` over an atom and then `Me` failed if the pointer drifted past the bond's middle onto the neighbouring atom, or off the molecule. `M` and `e` then ran tool shortcuts, and `e` chose the Eraser. On a zigzag chain the bond's hover zone is only 40–60% along a 22 px bond (measured in the #91 Windows build), so a small nudge was enough. This is the drift behind the "typing OMe deleted the chain" report.

**The rule** (ChemDraft key scheme; ChemDraw scheme unchanged). Once a label is in progress, the hover moving no longer ends it. The next key decides:

| Key typed mid-label | Result |
|---|---|
| A lower-case letter, a digit, or a capital that is not an element (`M` in OMe) | **Continues** the label on its atom, wherever the pointer is: a neighbour, another bond, or empty page. |
| A capital element letter, with the pointer still on the labelled atom or its own bonds | **Continues** the label (`CF3`, `NO2`), as before. |
| A capital element letter, after the pointer has left the atom and its own bonds | **Starts a new label** on the atom under the pointer, or on the nearer end of the bond under it. That includes the same atom on return, which keeps the existing leave-and-return behaviour. Over empty page it continues. |

Nothing continues once the labelled atom no longer carries the label, for example after an undo. A click, a tool change, or a key that cannot continue a label (Delete, Escape, punctuation) still ends the label, as before. So does every other change of context, now that leaving the atom no longer does:
- undo or redo from the menu;
- opening a document or starting a new one;
- a key that goes to a dialog or another text field;
- the window losing focus or being hidden.

## Files changed

- `apps/desktop/src/MainWindow.tsx`:
  - `hoverLabelContinuesForKey` (new, exported) holds the three rows above.
  - `hoverLabelAtomTargetForKey` sends a continuing key to the labelled atom from any hover target; before, only from the atom's own bond.
  - The on-atom continuation path uses the same test.
  - `assignHoveredNativeDeleteTarget` no longer ends the continuation when the hover moves. It only marks `leftAtom`.
  - `hoverRetargetedFromBondRef` is renamed `hoverRetargetedForLabelRef`. After the label commits, the hover returns to whatever is under the pointer.
  - The continuation is cleared in `restoreDocumentHistory`, in `clearDocumentInteractionState`, on the keydown early returns for a modal dialog and an ignored target, and on window blur and visibility loss (review follow-up, 94bf73c).
  - `CURRENT_BUILD_STAMP` is `10.10.20.57-opus`.
- `apps/desktop/src/hoverLabelTyping.dom.test.ts`: seven DOM tests.
  - These four fail on #91's code: a drift onto a neighbour, a drift onto empty page, `M` over another atom's bond, and a digit after a drift onto a neighbour.
  - These three pass on both and pin what must not change: a capital element over a neighbour starts a new label there (and continues there), a capital element over another atom's bond labels its nearer end, and an undone label does not continue.
- `hoverLabelTyping.dom.test.ts`, review follow-up: five more DOM tests, one per context change: undo then redo by menu, reopening a document with the same ids, a key in the Custom page size dialog, window blur, and a hidden window. All five fail without the fix.
- `apps/desktop/src/hoverLabelStress.dom.test.ts`: two stress tests (below). The wander test also asserts that the pointer left the labelled atom in at least half its trials.

## Stress test

The same 33-atom zigzag chain and seeded trials as #91. Each trial undoes back to the plain chain.

- **Drift:** hover an atom, type `O`, move the pointer 35%, 50%, 65% or 100% of the way to a neighbouring atom, then type `M` `e` Enter. A trial counts as passed only if that atom alone reads OMe, the tool is unchanged, and the structure is unchanged. In jsdom the pointer lands on the labelled atom at 35%, the bond at 50%, and the neighbour at 65% and 100%. The real app measured 0–35% atom, 40–60% bond, 65%+ neighbour.
- **Wander** (the original report): the pointer starts on the chain (an atom or a bond). Before each of `M` and `e` it moves up to 0.6 bond lengths in a random direction, onto neighbours, bonds or empty page. In 159 of 200 trials it left the labelled atom.

| 200 trials each | drift 35% | drift 50% | drift 65% | drift 100% | wander |
|---|---|---|---|---|---|
| #91 (a4c8276): labelled / tool switched | 50 / 0 | 50 / 0 | **0 / 50** | **0 / 50** | 159 / 41 |
| this branch: labelled / tool switched | 50 / 0 | 50 / 0 | **50 / 0** | **50 / 0** | **200 / 0** |

No trial changed the structure on either branch. CI runs 24 trials per test; set `HOVER_STRESS_TRIALS` for more.

## Tests run (Windows 11)

- `pnpm lint`: pass.
- `git diff --check`: pass.
- `vitest`:
  - `hoverLabelTyping` and `hoverLabelStress`: 34 passed.
  - `userFeedbackStress`, `atomLabelEditFocus`, `App.test.ts`, `keyboardShortcuts` and `eraserMolecule`: 307 passed.
- Full suite (`pnpm vitest run`):
  - 10a9eb3: **279 files, 5,340 tests passed, 0 failed** (33 skipped).
  - 94bf73c: 5,344 passed and 1 failed (33 skipped). The failure, in `unknownBondOrder.test.ts`, was a status line overwritten by "Native toolset windows unavailable" under full-suite load. It passes 3 of 3 alone and is a path this change doesn't touch.
- After the review follow-up (94bf73c):
  - `hoverLabelTyping` and `hoverLabelStress`: 39 passed;
  - `userFeedbackStress`, `atomLabelEditFocus`, `App.test.ts`, `keyboardShortcuts`, `eraserMolecule`, `agentBridge` and `drawingTools`: 329 passed.
- Undo, measured: a hover-typed `O` `M` `e` Enter is **one** undo entry, whether typed on the atom, over its bond, or after a drift onto a neighbour. Its status reads "Undid last document change" (an unlabelled entry, from #77's commit path, unchanged here).
- No Rust changes.

## Platforms

- **Windows:** verified in jsdom, as above, and in a launched release build of 94bf73c (`C:devowner-check-93`) with trusted CDP input on one launch:
  - owner steps 1–4: 6/6, 3/3, 2/2, 10/10;
  - #91's bond steps: 1/1 each.

  Details are in the PR comment.
- **macOS: unverified.** The change is shared TypeScript with no platform branch.

## For the owner: hands-on check

1. Draw a long chain with the Chain tool. Hover an atom and type `O`, move the pointer onto the next atom along the chain, then type `Me` and Enter. The first atom reads OMe, the second is unchanged, and the tool doesn't change.
2. Hover an atom and type `O`, move the pointer off the molecule onto empty page, then type `Me` and Enter. The atom reads OMe.
3. Hover an atom and type `O`, move onto the neighbouring atom, and type `N`. The neighbour becomes N and the first atom stays O.
4. Type `OMe` and Enter on the chain while moving the pointer a little between keys. One atom reads OMe, nothing is erased, and the tool doesn't change.

## Known limitations

- **No distance limit:** a lower-case letter typed after moving far away, without clicking, still continues the label. For example, `O` on an atom, a move across the page, then `e` gives "Oe", not the Eraser. A click or a tool change ends the label.
- **Only the key that opens the editor is affected:** once the label editor is open, keys go to it wherever the pointer is. That is unchanged.
- **ChemDraw scheme unchanged.**

## Follow-up: a drift right after the first letter (84fddb0)

The master session's Mac run at 4206dec found that `C`, a drift onto empty page, then `F` `3` turned the atom into "F3". The `F` was judged twice:

1. Against what the pointer was over (nothing), it correctly continued the label and moved the hover back onto the atom.
2. The on-atom path then judged it again, against that atom, and took it as a new label there.

The decision is now made once, against the pointer's own target. The rule above is unchanged: over empty page the label continues; over a different atom, a capital element letter starts a new label ("N on A, then O on B" stays two labels). Two DOM tests pin both cases. Windows reproduced the bug with real input on the 4206dec build; the rerun on 84fddb0 follows.

## Review

The first review requested changes: one medium and one minor finding, both addressed in 94bf73c. The scoped re-review of 94bf73c approved with no findings.

## One recommended next task

None from this change.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ab0ab2c31da2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.