# Issue

**Title:** #4447 - The Cancel option does not discard the name change

## Description

## Summary

Cancelling "Duplicate and Edit" (Cancel button or Esc) now brings back the preset that was active before the duplicate, instead of leaving the unsaved `_Copy` active. `duplicatePreset` replaced the active preset with the copy and nothing remembered the original, so Cancel restored the builder from the copy, and each further duplicate copied the copy (`A_Copy_Copy`).

```
state/rna-builder/rnaBuilderSlice.ts   presetBeforeDuplicate + startPresetDuplication
                                       setActivePreset and createNewPreset clear it, so it can't go stale
monomerLibrary/MonomerLibrary.tsx      duplicatePreset (builder button and preset context menu) uses the new action
RnaEditorExpanded.tsx                  onCancel re-activates the remembered preset
                                       the Esc listener depends on presetBeforeDuplicate; otherwise Esc ran an
                                       outdated onCancel that reset only the form
```

## Evidence

https://github.com/user-attachments/assets/dd7defd0-94a1-4f8d-904e-7592b9c98115

- **Before:** Duplicate and Edit on `A`, then Cancel: `A_Copy` stays active, and the next duplicate gives `A_Copy_Copy`.
  **After:** Cancel and Esc restore `A`, and the next copy is `A_Copy` again.
- New unit tests for the reducers and for Cancel; the Cancel test fails on master.
- Docker run of `rna-library.spec.ts` and `add-custom-preset.spec.ts`: one baseline changes on purpose ("After clicking Duplicate and Edit … Cancel, preset not saved" now shows the restored empty builder). Other diffs came from worker distribution and pass in isolation against the committed baselines.

### Verified in the app

RNA Builder in macromolecules mode, reproduced on master and checked with the fix:

- Cancel and Esc restore `A`.
- A context-menu duplicate restores the previously active preset.
- Cancel from an empty builder returns to the empty builder.
- Save still saves the copy.

## Merge Danger

**Door:** two-way

Only in-memory RNA Builder state changes: no file format, public API or saved-settings change.

**Blast Radius:** low

Limited to cancelling "Duplicate and Edit" in the RNA Builder (macromolecules mode). Saving a copy and all other preset editing are unchanged.

---

Memory bank: not needed

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `48af1b20d586`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.