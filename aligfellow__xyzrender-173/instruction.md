# Issue

**Title:** Add vibrational transition animations from frequency calculations

## Description

Direct animation of vibrational transitions from frequency calculations using `render_gif`.
`gif_vib=0`: zero-based selection of vibrational transition (ordered by increasing frequency)
`vib_scale=1.0`: scaling normal mode amplitude (default scaling normalized to a RMS displacement of 0.25 Å for displaced atoms) 
`vib_label=True`: displays calculated transition frequency on GIF.

Vibrational amplitudes are limited using interatomic distances to prevent bonded atoms from overlapping. 
Does not animate imaginary frequencies, refers to `gif_ts` instead. 
Vibrational animations can be combined with existing features (rotation, etc.).

Added description of feature to README.md

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `42f4c6bc1c20`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.