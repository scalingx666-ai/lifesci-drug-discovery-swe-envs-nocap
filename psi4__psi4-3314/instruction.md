# Issue

**Title:** Bump Einsums version

## Description

## Description
Bumping required version of Einsums needed to see if it resolves issues.

- [x] bump Einsums to v1.0.6 . there wasn't anything really wrong or different with Einsums capabilities, but for the conda package's baked-in min ver of a dependency wasn't compatible with the cmake detection of the dep in Einsums, so psi4 CI was failing
- [x] idk why Linux clang v11 (Oct 2020) suddenly took a dislike to b2 vibs and gave a wrong dimension error in `fd-freq-energy`, but v15 (Sep 2022) seems to fix it. We'll be bumping clang a bit to allow it to compile Einsums soon after v1.10 is released, so I don't feel too bad about anticipating the jump when so little was going wrong with v11.
- [x] all the Linux Azure lanes were failing the conda solve b/c hadn't accepted the license for main (non-c-f) channels. this is either a brown-out or very new. we don't actually use those channels, but I added the `conda tos` lines to fix it anyways.
- [x] `ENABLE_IntegratorXX` turned off b/c conda IntegratorXX incompatible with gauxc internal IntegratorXX build b/c of header install loc. not sure why this was working before unless hit a race condition on this PR
- [ ] I didn't mean to leave the `export KMP_DUPLICATE_LIB_OK=TRUE` in. It was necessary for the Linux Clang, similar to what we see with Windows omp. I already had automerge on, so will have to undo/fix this elsewhere
- [x] test `pvdz_adc2_any_6` was already excused on one of the Mac lanes. It started failing on Linux, too, probably with the new v0.16 release. should be investigated, but excusing for now
- [x] all the GHA timeouts of the three unix lanes were b/c qcfractal switched snowflake multiprocessing from fork to spawn in v0.62  . This was done for good warnings reasons, so not reverting right away. hang is locally reproducible and is b/c `An attempt has been made to start a new process before the  current process has finished its bootstrapping phase.`. probably real QCFractal use is ok, and it's just snowflake (used in psi4 testing) that's affected. avoiding v0.62 for now through codedeps
- [x] Schwarz vs. None screening started persistently failing on Windows, so I relaxed the tolerance a smidge to 3.e-11
 
## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `45385bb911de`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.