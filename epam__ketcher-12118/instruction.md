# Issue

**Title:** #4593 - Show not-allowed cursor on disabled Micro/Macro mode switch

## Description

## Summary

```diff
 .toggler-component-wrapper--disabled
   opacity: 0.4
-  pointer-events: none
-  cursor: default
+  cursor: not-allowed
+  & *  { pointer-events: none }
```

In "Modify in RNA Builder" mode the Micro/Macro switch is wrapped in `toggler-component-wrapper--disabled`. The wrapper had `pointer-events: none`, so the cursor never changed on hover (Undo/Redo/Layout are real disabled buttons and do show it). The wrapper now receives the hover and shows `not-allowed`; children stay non-interactive.

`packages/ketcher-macromolecules/src/styledComponents.ts`

## Evidence

- **Before:** wrapper computed style `pointer-events: none; cursor: default`
  **After:** wrapper `cursor: not-allowed`, inner button `pointer-events: none` (checked with Playwright on the built standalone app: Macromolecules → Sequence → select letters → Modify in RNA Builder). Headless screenshots don't render the cursor, so the icon itself wasn't visually captured.

## Merge Danger

**Door:** two-way

**Blast Radius:** Disabled mode-switch toggler styling only

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9ddfc4d140d9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.