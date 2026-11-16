# Issue

**Title:** Primitive cells in phonon-bandplot

## Description

Bugfix for #57 

The BORN file should contain a primitive cell, but Sumo was passing the full unit cell to Phonopy, leading to a mismatch in atom count (and, presumably, in coordinates...). The fix accesses an internal Phonopy attribute, which isn't ideal but seems the best option for internal consistency and minimal user input.

While fixing this, I also added support for the new(ish) Phonopy option `--primitive-axis=auto`, which may be accessed with `sumo-phonon-bandplot --primitive-auto`. A very welcome feature, this should make working with primitive cells less tedious.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6d1755db01fb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.