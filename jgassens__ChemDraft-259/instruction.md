# Issue

**Title:** Keep pasted structures and Clean Up from overlapping atoms in cages

## Description

## Summary

A Windows stress run found that pasting the 11-atom bridged cage `C1CC2CC3CC1CC(C2)C3` drew two atoms 0.15 bond lengths apart, and Clean Up Structure 2D then kept that drawing as "Selected structure already clean — … the generated layouts crossed bonds". This PR makes both paste and Clean Up refuse overlapping atoms, without slowing ordinary pastes.

- **Ranking** (`layout-engine`): atoms on atoms, atoms on bonds, overlapping collinear bonds and label collisions now outrank crossings when layouts are compared; crossings come next, then the soft geometry score. A bridged cage cannot always avoid crossings in 2D, so Clean Up now commits a crossing-only layout over a drawing whose atoms overlap. A small, bounded contact repair (at most 100 atoms, 1024 trials, 0.5 bond lengths) separates touching atoms in a cage projection when the rigid repairs cannot.
- **Clean Up status**: a drawing with a hard defect other than crossings is never reported as "already clean"; the status names the problem, for example "Clean Up couldn't fix the selected structure: the drawing still has overlapping atoms."
- **Paste**: every pasted SMILES (single or list entry) is checked for overlapping atoms, an atom on a bond, or overlapping collinear bonds. Only a depiction with one of those runs the same candidate selection Clean Up uses (shared code, with its identity and stereo read-back). Labels and crossings never trigger it. If nothing clears the overlap, the depiction is pasted with a warning. The standard layout is always kept as the deadline fallback, and the standard-only retry never runs alternates.
- **Label collisions, recalibrated** (shared with Clean Up, so this also changes main's behaviour): label-label overlap no longer counts between the labels of two directly bonded atoms (they sit beside their bond by design); non-bonded label pairs and labels against other bonds still count. Collision boxes follow the drawn ink (`atomLabelGlyphBounds`, reusing the label layout's run positions and advances) instead of the padded clipping box that bond clipping keeps using. Sans-serif labels use per-character extents from the Helvetica AFM data, named Courier fonts use 0.60 em per character, and anything else (other fonts, a bare `monospace`, characters outside the tables such as @, % or Greek capitals) uses the padded box, as main did.

Why the label change: measured on 100 ordinary molecules, 10 failed the original paste check, all on label-label overlaps (nitro N⁺ with O and O⁻, H₂N–NH, S–O, tetrazole N–N), and paste became about three times slower. On main the same false overlaps already send Clean Up of fused molecules such as tetrazolopyridine, a chloro-indazolone and hydrazobenzene to RDKit; after this PR they keep OpenChemLib's layout without loading RDKit.

Results (lengths in bond lengths; "main" is this branch with the paste check switched off, which is main's paste code exactly):

| Pasted | Main | This PR |
|---|---|---|
| Cage `C1CC2CC3CC1CC(C2)C3` | nearest atoms 0.15; 3 atom overlaps, 1 atom on a bond, 2 crossings | nearest atoms 0.76; no overlaps, 2 crossings |
| Rhodamine TMR | label/bond contacts only | unchanged (paste does not act on labels; Clean Up still fixes them) |
| Nitroaniline, nitropropiophenone, bis-hydrazide and the other 97 of a 100-molecule set | — | unchanged; none runs the alternate search |

Paste cost, 100-SMILES list through the list-paste kernel, 7 alternating rounds on a quiet machine: median 226.96 ms on main and 232.64 ms with this PR (+2.5%, 0.06 ms per entry); minima 218.17 and 224.17 ms. The cage alone takes 3.3 ms on main and 109.6 ms here, because it is actually repaired; TMR takes 10.4 and 10.9 ms. A before/after sheet of the cage, TMR and three control molecules was rendered with `pnpm -s chemdraft render-document` for review.

## Test expectation changes (existing tests)

| Test | Change | Reason |
|---|---|---|
| `packages/layout-engine/src/layoutQuality.test.ts`, incremental evaluator vs. its exhaustive reference | The reference skips directly bonded label pairs | The evaluator no longer counts them; the two must still agree exactly |
| same file, "uses renderer boxes for heteroatoms, isotope/charge labels and abbreviations" | Boxes equal `atomLabelGlyphBounds`; a new assertion keeps each inside the padded renderer bounds | Collision boxes now follow the ink |
| same file, "exempts only declared label pairs" | Raw overlaps `[[0,2],[0,3],[2,3]]` → `[[0,3],[2,3]]`; exempt `[[0,2],[0,3]]` → `[[0,3]]` | Atoms 0 and 2 are bonded; the declared exemption is still tested |
| `apps/desktop/src/documentWorkflow.test.ts`, zinc tetrakis(imidazole) metal placement | Recorded label contacts `[[Zn, N], [Zn, N]]` → `[]`; every other assertion unchanged | With ink-sized boxes the Zn and donor labels no longer touch |
| `packages/layout-engine/src/layoutRepair.test.ts`, "rejects the OMe swing whose turned label collides with isolated water" | Adds a second isolated water | With ink-sized boxes the base drawing had nothing left to repair; the second water gives it a real non-bonded label defect, and every rejection assertion is unchanged |
| same file, "bounds labelled repair … on 100 / 500 nitrogen atoms" | Initial label defects 3 → 2 | The oversized last label's contact with its bonded neighbour is now exempt; the repair still does real work (115 and 31 label plans) inside the unchanged time and plan limits |

## Tests run

On macOS, at `ecce5029` (main at `ac11a3f0` merged in; the tip only adds Reviewed-by lines to the same tree):

- `pnpm lint`: pass
- `pnpm vitest run`: 558 files passed, 10 skipped; 12,377 tests passed, 24 skipped, 0 failed
- `pnpm build`: pass
- `git diff --check ac11a3f0 HEAD`: clean
- `cargo fmt --check`, `cargo clippy --all-targets -- -D warnings`: pass
- `cargo test`: 641 passed, 9 ignored
- Packaged branch build `./run-app`, built without launching: `app/ChemDraft (dev).app` in the branch worktree, id `org.chemdraft.desktop.dev`, label `p8b [claude/p8b-cage-paste-gate]`, stamp `11.01.10.00-codex`

Reviews (each a separate agentctl run; no reviewer reviewed its own model's code; Reviewed-by lines are in each commit):

| Run | Reviewer | Scope | Outcome |
|---|---|---|---|
| run-20261101-083639-5cccf3 | Kimi, high | First change `c16408fe` | P1: a defective standard layout was dropped, so a slow repair could make the paste fail; P2: no chemistry round-trip test for the repaired-layout serializer; P3: an import cycle and a dead re-export. All fixed in `08a925ed` |
| run-20261101-091352-879eb7 | Kimi, high | `08a925ed`, the four test changes, the merge of main `7ef05e2a` (stamp only) | Earlier findings fixed. P2: the ink box used Helvetica advances for every font and too little descent. Fixed in `d93f3b04` |
| run-20261101-093528-5a8937 | Opus, high | `d93f3b04`, the three repair-test updates | No blocking findings. Low-medium: characters outside the advance table and a bare `monospace` could still be under-sized. Fixed in `ab7ec066` |
| run-20261101-094454-c63185 | Opus, low | `ab7ec066` | Accepted |

## Platforms

- **macOS:** the full test run, lint, build, cargo and a packaged no-launch build (see Tests run). Not checked by hand on screen.
- **Windows:** unverified by hand. The change is shared TypeScript with no platform branch; CI runs the tests on Windows. To check there: paste `C1CC2CC3CC1CC(C2)C3` and confirm no two atoms touch (crossed bonds are expected); paste nitroaniline `Nc1cc(N)cc([N+](=O)[O-])c1` and confirm it pastes as before; select the cage and run Clean Up Structure 2D and confirm the status does not say "already clean".

## Known limitations

- Bonded labels can still sit very close: at the default style the hydrazide and hydrazobenzene N–N labels are 0 to 0.26 px apart, so their bond is barely visible. Main draws them the same way; label placement is a separate follow-up.
- The "rejects the OMe swing" repair test does not prove the search ever generates the rejected swing (true before this PR as well).
- Ink extents come from the Adobe Helvetica and Courier metrics; the screen draws Arial and Courier New, which share their widths. Unmeasured fonts and characters fall back to the padded box.

Build stamp: `11.01.10.00-codex`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ac11a3f004b0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.