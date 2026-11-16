# Issue

**Title:** Preserve DCD timestep metadata on write (dt / NPRIV / NSAVC)

## Description

The DCD writer hardcodes `dt = 0`, `start = 0`, `step = 1` in the header, which means a write-then-read round-trip loses the integration timestep even when the source frames carry `time` and `simulation_step` properties. The TODO comment in `write_header` flagged this.

Fix the writer to derive the three fields from the `time` and `simulation_step` properties of the first two frames and seek back to patch the header at offsets 12 (NPRIV / start), 16 (NSAVC / step), and 44 (DELTA / dt). The pattern mirrors the existing back-patch of `n_frames_` at offset 8.

Also fix the reader to expose the absolute `simulation_step` as a frame property alongside `time`, matching the XTC / TRR / TNG / LAMMPS readers. Without this, a downstream writer has no way to recover the original step numbering.

When the source frames don't carry these properties, or when only one frame is written, the writer leaves the header values at zero — matching the previous behaviour.

Add a `TEST_CASE("DCD timestep round-trip")` to `tests/formats/dcd.cpp` with two sections: a positive case that writes four frames with explicit `time` / `simulation_step` and verifies the values survive a read-back, and a single-frame case that confirms the header is left untouched when `dt` cannot be derived. The byte-exact "write DCD files" test already covers the no-properties case.

Round-trip is bit-exact within DCD's f32 storage precision for `dt` (the header stores DELTA as float32, so the test computes its expected `delta` as `double(float(15 / 48.88821))` to match).

Tested end-to-end with a CHARMM-produced 266,680-frame trajectory (integration step 15 fs, NSAVC = 5000, NPRIV = 5000): every header field round-trips exactly.

Note: This change arose in the process of compressing files with mdcompress (https://github.com/refresh-bio/mdcompress), motivated by compression for uploads to MDrepo.org. This implementation was created with assistance from Claude Opus 4.7, with manual review/revision of proposed changes, and roundtrip validation in mdcompress.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c7344572226e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.