# Issue

**Title:** DCD: convert DELTA between AKMA and picoseconds

## Description

DCD's DELTA is in AKMA time units (CHARMM/NAMD convention), but the reader was storing it directly into timesteps_.dt and propagating it to Frame.time, which every other chemfiles format treats as picoseconds. Cross-format conversions (e.g. DCD -> XTC) silently inflated per-frame times by 1 / 4.888821e-2 ~ 20.45x.

I recently submitted PR #531, which back-patches DCD timestep metadata and correctly preserves NPRIV/NSAVC/DELTA through a DCD round-trip -- but that round-trip is symmetric, so a missing unit conversion on read paired with the same missing conversion on write cancels out and the bug stayed hidden. It only surfaces when reading DCD and writing XTC/TRR/etc.

Convert at the I/O boundary: multiply by AKMA_TO_PS on read, divide on write, in both the CHARMM-format (f32) and X-PLOR-format (f64) branches. timesteps_.dt is now in picoseconds everywhere in memory.

This matches how MDAnalysis handles DCD time units (DCD is AKMA on disk, ps in memory); see package/MDAnalysis/coordinates/DCD.py lines 81-82, 128, 153-154.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4cdb72ff8433`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.