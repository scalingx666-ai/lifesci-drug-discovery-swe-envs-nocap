# Issue

**Title:** Let tabs be renamed, from right beside their names in Settings ▸ Tabs

## Description

## What

Some screen titles are long for a tab bar ("Modeled Tolerance", "Modeled Tolerance & Receptors"), and the titles themselves stay as they are. So the user can name any tab whatever they like instead, for example shortening it to "Tolerance".

- **Settings ▸ Tabs:** every row, Search included, has a tinted **✎ Rename** capsule right after the tab's name, not tucked away at the trailing edge. It opens an alert with a text field prefilled with the current name. Once a tab is renamed, the alert also offers **Use Original Name**.
- **Renamed rows** show the tab's own title in small print underneath, so a renamed tab never loses what it is.
- **The bar** shows the name. The bar and Settings both label tabs through one function, `TabLayoutStore.label(for:)`. The screenshot and route tours still show the stock titles.

## Details

- **Storage:** names live apart from the layout, under `tabNames` as JSON keyed by storage key, so the layout's stored form is unchanged.
- **Backups:** the names are exported with the layout (`ExportedSettings`), reloaded after an import, and cleared by **Reset**.
- **Clearing:** an empty name, or the tab's own title, clears the name. Names are capped at 24 characters.
- **New strings:** four, in en, zh-Hans, zh-Hant, es and es-ES, using the words the tab settings already use (标签页 / 分頁 / pestaña).

## Testing

- New `TabLayoutStoreTests`: a name persists across a relaunch; empty, whitespace or the own title clears it; the 24-character cap; Reset clears names; an import's names are picked up on reload.
- `ExportCoverageTests` and `ExportRoundTripTests` pass with the new key.
- Checked in the simulator, in the default skin and in Hebi.
- Built and tested in a checkout whose tab files are identical to `main`'s. This branch itself wasn't built locally, because swift-collections 1.7.1 on `main` doesn't compile with the local Xcode 27 beta; CI will build it. For the same reason the catalog's reordering step didn't run, so the four keys are appended rather than sorted, and Xcode will sort them on its next build.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8740b3a3fc11`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.