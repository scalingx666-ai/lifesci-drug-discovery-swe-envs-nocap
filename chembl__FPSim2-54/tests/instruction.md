# Issue

**Title:** command-line driver for FPSim functionality using 'python -m FPSim2'

## Description

This PR adds a way to access FPSim2 functionality from the command-line using "python -m FPSim2" followed by a subcommand. Here is the output from `python -m FPSim2 --help`:
```
usage: FPSim2 [-h] {create,import,export,search,substructure,distmat} ...

FPSim2 driver

positional arguments:
  {create,import,export,search,substructure,distmat}
    create              create an FPSim2 data set from a structure file
    import              import RDKit fingerprints in FPS format
    export              export the fingerprints to FPS format
    search              Tanimoto or Tversky search
    substructure        substructure screen
    distmat             generate symmetric distance matrix and save in SciPy's sparse 'npz' format
```

I had several goal in mind when writing this new code:

1. Add import/export support for the FPS format, which I have been promoting as a common format for fingerprint exchange.

2. Provide a chemfp-like API so those in search of a no-cost open source replacement for chemfp under Python 3 could have an easier migration path, while not straying far from the FPSim2 approach.

3. Have some way to break down search performance numbers (via `--times`) in a way which makes it easier to understand where FPSim2 spends it time.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e3782264b78e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.