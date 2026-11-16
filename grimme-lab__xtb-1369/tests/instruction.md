# Issue

**Title:** fix issue 889

## Description

This should address issue #889 .

I made the iter_needed variable which tracks the number of needed iterations needed to complete the geometry optimization an optional variable, as this feature is only of interest for the --grad option and not for example the docking. Making it not optional would further neccesiate to change every geo opt driver call which is in my option not necessary. It is initialized to 0 and not 1 as also the geometry optimization iter starts counting at 0 and when for the unoptimized geometry the grad is requested this corresponds to iter = 0.

For me the build and testsuite worked using the meson build system with ifort compiler.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `08cc69403357`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.