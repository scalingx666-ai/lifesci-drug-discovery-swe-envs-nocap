# Issue

**Title:** cuEST wK progress

## Description

- Exposed usage of range-separated (rs) functionals (energies only) by configuring `cuest_df_plan_` in `cuESTJK.cc` with range separated parameters. As of opening this PR, rs functional energies computed with the cuEST backend are not currently within the acceptable error range set for other functionals in `test_cuest.py`

- Created an option to toggle between cuEST's default mixed precision emulation (intended to boost performance) and usage of full double-precision throughout. Note that while emulated energies match full precision very closely (when using cuEST), there is still some discrepancy between the values calculated by cuEST vs by Psi4. The cause of this has not yet been fully resolved. 

- Fixed bug in which non rs functional gradients were scaled by HF exchange fraction twice, inadvertently caused by configuring rs parameters in `cuESTJK.cc`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4a24fa5913b9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.