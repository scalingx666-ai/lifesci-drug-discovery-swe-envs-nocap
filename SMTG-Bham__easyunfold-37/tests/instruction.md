# Issue

**Title:** Update commensurability warning

## Description

As discussed @zhubonan;

> I think the check for the commensurability of the primitive and supercell in easyunfold is too strict. For instance, if one is doing easyunfold calculations for a SQS supercell which has been relaxed, and so has slightly different cell parameters, then this will print a warning saying the primitive and supercell are not commensurate which can be confusing for users. I know if the volumes are very different then this could impact the quantitative accuracy of the Brillouin Zone spacing, but I think this is likely a relatively minor effect in most use cases and we should have a certain tolerance for this (greater than the np.allclose default of 0.001%). Example of what I mean here:

![image (21)](https://github.com/SMTG-Bham/easyunfold/assets/51478689/574a6680-3bc9-44fa-ac31-345695b08766)

> A relative tolerance of a couple percent should be fine? You likely know more about at what level of mismatch this would become significant enough to warn the user. Could have a two-level warning where if the match is close but not very good, it warns saying there will be some quantitative innaccuracies, or if very large mismatch then more severe warning

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `037c09a1748f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.