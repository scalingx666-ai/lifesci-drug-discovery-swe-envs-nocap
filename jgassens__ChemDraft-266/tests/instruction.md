# Issue

**Title:** Keep rings attached at a bonded atom on the page

## Description

Since the largest-open-angle ring placement landed, a ring attached at a bonded atom could be drawn partly off the page. This affected the 3, 6 and 7 hover keys, a ring-tool click on an atom, and the ring sprouts and fuses that share the path. For example, a benzene on the right-hand carbon of a bond near the right edge reached past the page border.

## What changes
- **Open space is unchanged:** the preferred (largest-open-angle) orientation is used whenever the whole ring fits on the page, so toluene, methylcyclohexane and methylcyclopentane keep their symmetric placement.
- **Near an edge**, the ring is turned about the attachment atom in 15° steps. A turned placement is used only if every angle between an existing bond and each new ring bond is at least 90° (no cramped rings), the whole ring is on the page, it stays at least 0.45 bond lengths from existing atoms, crosses no existing bond and encloses no existing atom. The most symmetric qualifying placement wins. A hexagon therefore needs about two bond lengths of room beside the atom; closer than that, the attachment is refused rather than drawn badly.
- **If nothing fits**, nothing is added and the status ends "the page edge blocks every direction". A blocked ring-tool click now shows that reason too, instead of a generic message, and adds no undo entry.
- Clearance, crossing and enclosure are checked against the molecule the ring is attached to. Separate molecules or other objects on the page are not avoided, the same as ring placement in open space on main; avoiding other objects is a follow-up.
- Only the newly created ring atoms are checked against the page, so an atom that already sits outside the page can still take a ring.
- The geometry helpers (`ringAttachmentRotationAims`, `ringAttachmentAngleMetrics`, `selectRingAttachmentRotation`, `layoutPointsFitBounds`, `ringAttachmentIsClear`) live in layout-engine.

## Tests
- New: the 3/6/7 hotkeys and the benzene tool at 38.5 units from the right edge (turned ring, angles asserted: 90/150 for hexagons, 126/126 for cyclopentane) and at 21.5, 28.5 and 33 units (refused, document unchanged); obstacle tests where one turned placement is blocked (the mirror turn is used) and both are blocked (refused); a 0.01° angle tolerance test; a clean fallback at a two-bond atom (no overlap, no crossings); a no-fit refusal with the document unchanged; a blocked ring-tool click (page-edge text, no undo entry); a source atom outside the page; layout-engine tests for candidate order, clearance, crossings, collinear overlap and enclosure.
- The existing open-space placement tests are unchanged.

Local gauntlet (lint, vitest, build, diff check, cargo fmt/clippy/test) and a packaged build run before this leaves draft. Hands-on runbook on macOS and Windows: `_master-scratch/screen-runbooks/ring-attach-page-clamp.md`.

## Platforms
- **Windows** at 88e895c3: runbook steps 1–4 passed. A turned hexagon needs about 41.5 units of room: at 41.5 units it is turned up with 90/150 degrees, at 43.5 units 105/135, and at 21.5 units it is refused. Step 5 assumed separate molecules are avoided; they are not (see above), so that step was dropped from the runbook.
- **macOS** at 88e895c3: runbook steps 1–4 passed. The normal ring still fits at about 44 units; at about 37.5 units the 3 and 6 keys turn the ring to 90/150 degrees, regular and on the page, and 7 places a pentagon on the page; at one bond length 3, 6 and 7 are refused with "…the page edge blocks every direction"; the ring tool refuses at one bond length with no undo entry and places a turned ring at two.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d3a652767b71`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.