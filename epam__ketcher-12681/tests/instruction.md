# Issue

**Title:** #11972 - Switch to DNA hotkey on macOS is already being used to show/hide the Dock

## Description

## Summary

On macOS, the DNA typing-type hotkey `⌘+Option+D` is taken by the OS (show/hide the Dock), so Ketcher never receives it.

The sequence-type hotkeys in `hotkeysConfiguration` now bind `Ctrl+Alt` first (`Ctrl+Option` on macOS) and keep `Mod+Alt` as a second binding. This restores the v3.18 binding that #10453 (`2c8aba9ca1`) changed to `Mod+Alt`. Windows and Linux are unchanged.

```diff
 // packages/ketcher-core/src/application/editor/editorEvents.ts
-RNASequenceType:     shortcut: ['Mod+Alt+r']
-DNASequenceType:     shortcut: ['Mod+Alt+d']
-PEPTIDESequenceTYpe: shortcut: ['Mod+Alt+p']
+RNASequenceType:     shortcut: ['Ctrl+Alt+r', 'Mod+Alt+r']
+DNASequenceType:     shortcut: ['Ctrl+Alt+d', 'Mod+Alt+d']
+PEPTIDESequenceTYpe: shortcut: ['Ctrl+Alt+p', 'Mod+Alt+p']
```

The tooltip text comes from the first shortcut in each list, so on macOS it now reads `Ctrl+Option+D`. That matches `documentation/help.md` and `openspec/specs/macromolecules/spec.md`, which already say `Ctrl+Alt+R/D/P`.

## Evidence

- **Before:** `sequenceTypeHotkeys.test.ts` fails 6 of 12. On macOS, `Ctrl+Option+R/D/P` matches no action, and the tooltip reads `⌘+Option+D`.
  **After:** 12 of 12 pass. The ketcher-core suite passes: 1228 passed, 12 skipped. `tsc --noEmit`, ESLint and Prettier are clean.

```
on macOS:   keydown(KeyD, ctrl+alt) -> DNASequenceType     // was: no match
on macOS:   keydown(KeyD, meta+alt) -> DNASequenceType     // still works
on macOS:   tooltip(DNASequenceType) == "Ctrl+Option+D"    // was "⌘+Option+D"
on Windows: keydown(KeyD, ctrl+alt) -> DNASequenceType, tooltip "Ctrl+Alt+D"  // unchanged
```

### Verified in the app

Macromolecules mode, Sequence layout, Chrome on macOS, local `dev:standalone`:

- **Before:** tooltip `DNA (⌘+Option+D)`. `Ctrl+Option+D` does nothing, and `⌘+Option+D` toggles the Dock.

<img width="1000" height="240" alt="before" src="https://github.com/user-attachments/assets/b0c766f6-dbf0-4667-ae71-8ca88dc4f94a" />

- **After:** tooltips `RNA (Ctrl+Option+R)`, `DNA (Ctrl+Option+D)`, `Peptides (Ctrl+Option+P)`. Each combination selects its type, and `⌘+Option+R` still selects RNA.

<img width="1000" height="240" alt="after" src="https://github.com/user-attachments/assets/1a123b1d-9c62-481f-a5ec-4cc15516339f" />

## Merge Danger

**Door:** two-way

Only the key bindings and tooltip text change. Nothing in KET/MOL output, the public API, or local storage changes.

**Blast Radius:** small

Macromolecules sequence mode only. MacOS users get Ctrl+Option (the old ⌘+Option still works). This reverses the macOS tooltip that #10453 asked for.

---

Memory bank: not needed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cb3395345475`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.