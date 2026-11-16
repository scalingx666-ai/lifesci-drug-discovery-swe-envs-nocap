# Issue

**Title:** #5089 - Phosphate is displayed wrong in the Sequence mode, if connect phosphate R2 and unsplit nucleotide R1

## Description

https://github.com/user-attachments/assets/66bf325d-9399-4408-a2a4-b242d0a261fa


## Summary

A single phosphate connected by R2 to an unsplit nucleotide's R1 was shown as `@` in Sequence mode instead of `p`. `Chain.add` keeps a phosphate as a phosphate node only when the next monomer is a nucleoside, nucleotide or peptide. Unsplit nucleotides were accepted before a phosphate but not after it, so it became a linker node, which is drawn as `@`.

```diff
 // ketcher-core  domain/entities/monomer-chains/Chain.ts
-      return isNucleosideOrNucleotide || nextMonomer instanceof Peptide;
+      return (
+        isNucleosideOrNucleotide ||
+        nextMonomer instanceof UnsplitNucleotide ||
+        nextMonomer instanceof Peptide
+      );
```

This follows the rule from #4607: a single phosphate shows as `p`, and a group of two or more shows as `@`. A phosphate between two unsplit nucleotides therefore also changes from `@` to `p`.

## Evidence

- **Before:** `hn` R2 to `5SUPT` R1 shows `@ X`.
  **After:** `p X`.
- `Chain.test.ts`: phosphate before an unsplit nucleotide, and phosphate between two unsplit nucleotides, fail on the previous code (`LinkerSequenceNode`) and pass now. Phosphate after an unsplit nucleotide, and two phosphates before one (a single `LinkerSequenceNode`), pass on both.

### Verified in the app

Macromolecules, Sequence mode, structures loaded from HELM:

| Chain | Result |
|---|---|
| Phosphate → unsplit | `p X` |
| Unsplit → phosphate → unsplit | `X p X` |
| Unsplit → phosphate | `X p`, unchanged |
| Two phosphates → unsplit | `@ X`, unchanged |
| Phosphate → CHEM | `@`, unchanged |

Next to the new `p`, the right-click menu opens, typing `A` gives `A X`, Undo restores `p X`, and switching to Flex and back keeps it.

## Merge Danger

**Door:** two-way

Sequence mode display only: no file format, public API or saved-settings change.

**Blast Radius:** low

Only a single phosphate directly before an unsplit nucleotide changes, in Sequence mode. Sequence-mode screenshots containing that combination would need new baselines.

---



Memory bank: not needed

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `090cf8288dec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.