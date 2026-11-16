# Issue

**Title:** Restore missing MMFF94 class-2 (2-2-2) stretch-bend parameter

## Description

mmffstbn.par was missing the class-2 stretch-bend entry for atom types (2,2,2) (sp2 carbon center with both bonds BT-flagged) that is present in the original MMFF94 parameter set. Without it, class-2 C(sp2)-C(sp2)-C(sp2) angles fall through to the MMFFDFSB default (0.30/0.30) instead of the fitted values (0.219/0.250).

Verified against an independent transcription of the original file (Tinker's mmff94.prm): it is the only missing entry among 283, with no value differences in the rest. Energy impact on the Halgren validation suite (JIYJAC): stretch-bend 0.2368 kcal/mol vs 0.1858 from the original BatchMin program; matches to 4 decimals once the entry is restored.

Inserted after the class-1 (2,2,2) entry to preserve the canonical CXBA ordering.


## Summary by Sourcery

Bug Fixes:
- Add the missing class-2 C(sp2)-C(sp2)-C(sp2) stretch-bend entry so these angles no longer fall back to the generic MMFFDFSB default parameters and instead use the fitted MMFF94 values.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0e94434fa75c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.