# Issue

**Title:** Make ring bond markers more lenient towards branching

## Description

@tylerjereddy I still missed one in #60.
In all cases ring bonds should be made to anchors (`anchor`), rather than simply the previous atom (`idx-1`). If normal atoms are added, these automatically become the next anchor, which means that "normal" operations are not affected. The change is in everything branch related. This should fix all `...)1..1` and `..1..)1` flavoured ring markers.

I also added extra coverage tests in `tests/test_smiles_helpers.py` to exercise previously untested `smiles_helper.py` edge cases and bring that module's coverage to 100%.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4f32c4c51001`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.