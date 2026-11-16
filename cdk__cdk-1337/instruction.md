# Issue

**Title:** removeBond keeps the double bond configuration when it changes carrier

## Description

When removeBond deletes a carrier bond of a double bond stereo element, the element moves to the other bond on that atom but keeps its TOGETHER/OPPOSITE value, so it then describes the other isomer. In `F/C(Cl)=C/C`, removing the C-F bond and then the F gives `C/C=C/Cl`; removeAtom on the F alone gives `C/C=C\Cl`.

The configuration is now inverted when the carrier changes, as removeAtom already does. `deletingBondUpdatesCisTrans3` expected the flipped isomer and is corrected.

The test commit fails without the fix.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `09f97ebc722d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.