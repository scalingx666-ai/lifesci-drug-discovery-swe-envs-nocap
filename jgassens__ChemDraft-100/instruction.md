# Issue

**Title:** Status row: the build stamp no longer runs into the status or the warnings count

## Description

## Summary

**This PR is stacked on #90** (base `claude/open-warnings-list`), and will be retargeted to `main` once #90 lands.

At the document window's 900 px minimum, the build stamp at the bottom right ran into the status text and over the **"N warnings"** link that #90 adds. #90's Windows owner-step screenshot showed it.

The cause:
- the status line sat at the bottom left with a fixed `max-width: calc(100% - 240px)`;
- the stamp sat separately at the bottom right;
- a branch build's stamp carries the worktree label (`Build 10.10.19.47-opus · beautiful-darwin-80c177 [claude/…] · <date> <hash>`), which is much wider than 240 px;
- so whenever the status was long, the two overlapped. The overlap already existed for long status text; #90 put a clickable target there.

**Fix:** one flex row (`.status-row`, `data-status-row`) along the bottom of the workspace:
- on the left, `.status-row-main` holds the status, the warnings count and the modifier hint. It grows and shrinks (`flex: 1 1 auto; min-width: 0`). The status text and the hint end in an ellipsis, and the warnings count never shrinks;
- on the right, the build stamp keeps its own measured width (`flex: 0 0 auto`, nowrap);
- so the two can't overlap at any width. The row keeps `pointer-events: none`, and only the warnings button takes clicks, as before.

No text, attribute or behaviour changes otherwise: `data-status-message`, `role="status"`, `data-modifier-hint` and the stamp's content are all unchanged.

## Tests

- **`apps/desktop/src/statusRow.dom.test.ts` (new, 3 tests):**
  - the status, the "11 warnings" count and the stamp sit in one `data-status-row`, the stamp last, with exactly one of each;
  - App.css keeps the layout contract: `.status-row` is a flex row from left 8 px to right 8 px, `.status-row-main` is `flex: 1 1 auto; min-width: 0`, the status and hint truncate with an ellipsis, and `.build-stamp` and `.open-warnings-button` are `flex: 0 0 auto`;
  - pointer events go through the row to the canvas (`.status-row` is `pointer-events: none`) except on the warnings count (`auto`).
- jsdom has no layout, so the layout itself was checked in a browser. That run used the web dev server in headless Edge (Chromium, the engine WebView2 uses) at **900×640 CSS px, DPR 1 and 2**. Each case had a long file name in the status (`Opened a-very-long-reaction-scheme-file-name-…cdxml as external CDXML subset with 11 warnings`) and the warnings count present. The three cases:
  - this branch build's real long stamp;
  - a stable build's short stamp (`Build 10.10.23.40-opus · 2026-10-10 23:40:12 abc1234`);
  - an extra-long branch stamp.

  **All 6 pass:**
  - the status group ends at or before the stamp's left edge;
  - the stamp is never clipped;
  - the warnings count stays whole: at DPR 1 with the branch stamp it spans x = 321–380 and the stamp starts at 392; with the short stamp, the count spans 583–642 and the stamp starts at 654;
  - the status text is ellipsized each time.
- `docs/manual-stress-checklist.md` has a new status-row entry.

## Platforms

- **Windows:**
  - `pnpm lint` ✅;
  - the new test and the status-related DOM suites ✅ (`openWarnings`, `placementSnap`, `freehandArt`, `atomLabelEditFocus`: 5 files, 144 passed);
  - `git diff --check` ✅;
  - the headless-Edge layout check above ✅.
- **macOS:** not verified. It's plain flexbox in WKWebView with nothing platform-specific. Check a branch build and a stable build at the minimum window size.

## Gates

- [x] Stress test (layout check at 900 px, DPR 1 and 2, three stamp lengths)
- [x] Review: claude-fable `fable-pr100-20261010` APPROVE. Its two nits are fixed in the follow-up commit (pointer-events pinned in the contract test, the stamp's redundant `margin-left: auto` dropped), and the layout check still passes all 6 cases. Quick check `fable-pr100-rr-20261010` APPROVE.
- [ ] Retarget to `main` after #90 lands
- [ ] macOS check

## Squash-merge message

```
Status row: the build stamp no longer runs into the status or the warnings count

The status (bottom left, with a fixed max-width) and the build stamp
(bottom right) were positioned apart, so a long status or a branch
build's long stamp (it carries the worktree label) ran one into the
other, and over the "N warnings" link. They now share one flex row: the
status and the modifier hint shrink and end in an ellipsis, the warnings
count and the stamp keep their width.

```

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e0abfeba1e1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.