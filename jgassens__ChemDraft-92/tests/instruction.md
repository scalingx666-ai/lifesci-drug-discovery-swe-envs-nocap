# Issue

**Title:** Ring placement never leaves an over-valent atom

## Description

## Summary
Clicking a ring tool (cyclohexane, benzene and the other ring templates) on a bond fused the new ring even when an endpoint of that bond had no free valence, leaving a five-bond carbon with the status "Fused cyclohexane template". The chemistry changed silently (AGENTS.md §7).

One guard now covers every ring placement that changes an existing molecule: bond fusion, closure onto a neighbouring ring, and spiro attachment. It applies to clicks, the hover preview, and ring hotkeys. It judges the finished molecule, not a prediction: every existing atom whose valence use (bond orders plus radicals) rose must still be allowed at its element and formal charge. So an aromatic template that raises a shared bond's order is caught too.

- **A refused click** places the ring separately, as the atom branch already did. The status line names the reason: "an atom on that bond has no free valence" or "the ring would close onto an atom with no free valence".
- **A refused ring hotkey** (pressing a ring key over a bond or atom) changes nothing. The status line says why.
- **Atoms whose label has no element** (OMe, R) are skipped, as every valence check skips them.

## Behaviour changes
- A **benzene** ring sharing one atom with an existing ring (a spiro attachment), on a ring carbon or a neutral N, is now placed separately. Before, it was committed with that atom over-valent (five bonds on the carbon). A saturated spiro ring such as cyclohexane still attaches.
- Benzene fused onto the central bond of an s-cis diene is now placed separately, because the aromatic re-pairing would double the shared bond past an endpoint's valence. Before, it was committed over-valent.
- Two existing tests had asserted those over-valent results (spiro benzene on a ring carbon, and on a neutral N). They now use the legal cases.

## Tests
- `userFeedbackStress.dom.test.ts` scenario C's `it.fails` (ring click on a full-valence bond endpoint) now passes.
- New: 8 `documentWorkflow` unit tests (one or both endpoints saturated, charged endpoints, aromatic shared-bond order rise, closure onto an over-valent reused atom, abbreviation-labelled endpoint, plus regressions: naphthalene, fused cyclohexanes, legal spiro).
- New: a ring-hotkey DOM test.
- New: a seeded 40-click stress test.

## Stress numbers (real pointer events, macOS host)
| Scenario | Result |
|---|---|
| C: 40 seeded ring clicks over saturated, aromatic and ordinary molecules, 3+ templates | 17 atom clicks, 23 bond clicks; 16 refused and placed separately, 13 fused, 1 closure, 10 spiro; 21 molecules; **0 over-valent atoms**; 2145 ms |
| C bond: ring click on a 4-bond endpoint | endpoint keeps degree 4, ring placed separately (2 objects); 10 ms |
| C bond hotkey: ring key over that bond | nothing changed (1 object); 8 ms |
| C refusal kinds | 5 refusal kinds, 20 clicks, 20 separate rings; 419 ms |

Timings are logged, never asserted.

## Gauntlet (macOS)
- `pnpm lint`: pass
- `pnpm vitest run`: **5346 passed**, 17 skipped, 0 failed
- `pnpm build`: pass
- `git diff --check`: pass
- `cargo fmt --check`: pass

No Rust changed, so clippy and cargo test are left to CI on macOS and Windows.

## Platforms
- **macOS:** gauntlet above.
- **Windows:** unverified by hand. The change is shared TypeScript with no platform branch; CI runs the Windows suite.

## Known limitations
- Benzene on a diene's central bond is refused rather than given a correct double-bond pattern. The root cause is in the aromatic re-pairing step (`sharedBondContributesAromaticPi`). Refusing is the safe behaviour until that is fixed.

## Review round 1 (Kimi, kimi-pr92-20261010): fixes in a23cd9d6
1. **No false spiro refusals.** The early "+2 bonds" spiro check could refuse placements the final check would allow: a benzene spiro actually adds +3, so legal spiros on S (becoming S(IV)) and P (becoming P(V)) were refused. It is gone, and the result guard alone decides. The early measure now only names why a spiro that drew nothing failed.
2. **The '0' ring-closure hotkey** goes through the same guard. A closure that would over-fill the closure atom changes nothing and says why.
3. **Every ring-hotkey refusal has its own reason:** an abbreviation label ("relabel it to an element first"), an uneditable structure, an unavailable target, or ring geometry that cannot be placed.
4. **Separate wording** for an atom over-filled only by an aromatic template's double-bond re-pairing, distinct from a ring closing onto an atom.

Not fixed (cosmetic, by the coordinator's decision): a refused plan's ghost preview can shift a few pixels.

Gauntlet at a23cd9d6 (macOS): lint pass · vitest **5352 passed**, 0 failed · build pass · diff --check pass · cargo fmt pass.
New stress lines: `[stress C hotkey reasons] keys=2 abbreviation=1 geometry=1` · `[stress C cyclic closure] keys=2 refused=1 closed=1` · the 40-click run is unchanged (16 refused, 13 fused, 1 closure, 10 spiro, **0 over-valent**).

## Windows hands-on pass: fix in 5608fbcd
On a four-bond star built with real clicks (one Bond click, then three on the same atom), the ring could not be drawn, and the geometry reason was reported ("that bond cannot accept a ring" / "the ring's geometry could not be placed there"), suggesting another spot might work. The full atom is now reported first, on the tool click, the preview and both ring hotkeys, through one helper (`nativeRingTargetFailureValenceReason`). The geometry reason remains when the atoms do have room. New DOM test on that clicked star, macOS and Windows: `[stress C clicked star] click=1 hotkey=1 spiro=1 PASS`.

Gauntlet at 5608fbcd (macOS): lint pass · vitest **5354 passed**, 0 failed · build pass · diff --check pass · cargo fmt pass.

## Squash message (ready)
```
Ring placement never leaves an over-valent atom (#92)

Clicking a ring tool on a bond fused a ring even when an endpoint had no
free valence, leaving a five-bond carbon. One guard now judges the finished
molecule for every placement that changes an existing structure (bond
fusion, closure onto a neighbouring ring, spiro attachment, the '0'
cyclic-bond closure) on clicks, previews and hotkeys alike: every existing
atom whose valence use rose must still be allowed at its element and
charge. A refused click places the ring separately and the status line says
why (a full atom is named ahead of a ring that has no room); a refused
hotkey changes nothing and names its reason.

```

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b0c35b389a5c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.