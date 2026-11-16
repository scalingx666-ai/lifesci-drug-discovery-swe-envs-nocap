# Issue

**Title:** feat: rewrite LAMMPS trajectory reader

## Description

The new implementation allows reading and writing of the LAMMPS dump/atom format. This format is customizable and we can handle the most common custom attributes: units, time, masses, charges, names, and velocities.
Writing is also relatively complex. This implementation writes unwrapped coordinates which is not part of the atom style, but rather the custom variant. My understanding is that all atoms in the `atom` dump _must_ be wrapped, so using the `custom` style is faster for us. This also writes always mass and charge because there is no reliable way to detect whether it is explicitly set or the default of 0. #288 might help here in the future.
The handling of scaled coordinates is taken from [this part in molfiles](https://github.com/chemfiles/molfiles/blob/df74add3f1dc0fdc0a06e9e5200425b4241a09ec/src/lammpsplugin.c#L1280-L1327). Haven't really checked from 'first principles' if this conversion makes sense.

This  and ticks a box in #154.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cc18cdd4675c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.