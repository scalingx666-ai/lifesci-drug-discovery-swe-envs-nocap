# Issue

**Title:** Fix CalcEnrichment for unsorted fractions and fractions reaching the end

## Description

#### Reference Issue

#### What does this implement/fix? Explain your changes.
`Scoring.CalcEnrichment` walks the score list once and consumes one fraction each time it passes a cut-off. That only works when the fractions are sorted in increasing order and fall on different positions, and when no cut-off is the last molecule:

- unsorted fractions get the value of another cut-off: with 10 molecules, `[0.5, 0.1]` returns the top-6 value for `0.1` instead of the top-1 value;
- fractions that fall on the same position (`0.11` and `0.12` with 10 molecules, both top 2) shift the following values;
- a fraction whose cut-off is the whole list, such as `1.0` or the `0.9` with 5 molecules from #7981, is dropped, so the result is shorter than `fractions` and can be empty.

This counts the actives cumulatively once and then computes each fraction on its own top `max(1, ceil(numMol * f))` molecules. The result always has one value per fraction. The existing cases in `UnitTestScoring.py` (best/worst case, all actives, all decoys, a fraction below one molecule, `0.0`) give the same values as before.

New test `test1_enrichment_factor_fractions`: the five fractions `[0.5, 0.1, 0.11, 0.12, 1.0]` on 10 molecules against the definition, and the #7981 example (now `[1.0]` instead of `[]`). It fails before the change and `UnitTestScoring.py` passes after it. I ran it with the latest `rdkit` wheel from PyPI, whose `Scoring.py` is identical to master, with the patched module copied in; I did not build RDKit from source.

#### Any other comments?
AI use: this change, the test and this description were prepared with Claude Code (Claude Opus 5.5).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `73268ba001e8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.