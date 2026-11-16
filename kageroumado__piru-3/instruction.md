# Issue

**Title:** feat(timeline): toggle + threshold for stacked-lane sessions

## Description

## Summary

The timeline switched a busy session from overlapping curves to stacked per-substance lanes ("small multiples") at a **hardcoded 4 distinct substances**, with no way to disable it or tune the cutoff. This adds two user preferences under **Settings → Journal**:

- **Stack Busy Sessions** — master toggle for whether stacked lanes are ever used. When off, every curve is always overlaid on one graph regardless of substance count.
- **Stack From** — stepper (range 2–8) for how many distinct substances trigger lanes. Shown only when the toggle is on; value rendered as a bare number.

Both prefs are stored in the app-group suite (`group.dev.yumeji.piru`) so the widget / Live Activity honor the same choice as the main app.

## Implementation notes

- New `LaneModeDefaults` enum in `Shared/TimelineGraphView.swift` is the single source of truth for the keys, defaults, and stepper range.
- `TimelineGraphView.laneMode` now gates on the live values via `@AppStorage` (lane mode is presentation-only, so it stays out of the curve-geometry cache key `DerivedKey`).
- The two host views that size their graph card by the threshold — `SessionDetailView.graphHeight` and `ActiveSessionHeroCard.multiGraphHeight` — read the same prefs, so card height and the graph's lane decision can't disagree.

## Localization

- Added en / zh-Hans / zh-Hant for the 3 new strings via `translate_catalog.py` (session terminology matches the app's existing 记录 / 記錄).
- The threshold readout uses `Text(_, format: .number)`, so it localizes for free and adds no catalog key.
- Also fixed `translate_catalog.py`'s stale hardcoded `project_root` to resolve relative to the script file.

## Testing

- `xcodebuild -scheme Piru -destination 'platform=iOS Simulator,name=iPhone 17 Pro' build` — **BUILD SUCCEEDED** across all targets.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `097491dba27a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.