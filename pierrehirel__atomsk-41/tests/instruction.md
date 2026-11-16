# Issue

**Title:** Fixed min and max coordinates in lammps output

## Description

The lammps file output is incorrect if the whole system has been rotated > 90 degrees, since the minimum coordinate becomes larger than the maximum coordinate.

For example the following generates an invalid lammps output file
```bash
atomsk --create bcc 3.3026 Ta -rotate Y 180 tantalum.lmp lammps
```

This PR fixes the aforementioned bug.

Contact info:
Eerik Voimanen
eerik.voimanen@tuni.fi
Research assistant
Tampere University

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `380fbe9767ce`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.