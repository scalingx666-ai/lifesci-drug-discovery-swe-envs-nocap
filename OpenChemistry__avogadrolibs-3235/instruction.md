# Issue

**Title:** Fix: Alt for larger steps, and no change signal for ignored keys

## Description

fix #3188

## Summary
- Add a check to the `AutoOpt::keyPressEvent` to detect when an Alt and a movement key are pressed, and change the movement from 0.1 A to 0.5 A.
- Add a check to see whether atoms have moved before calling `emitChanged` to prevent unused keys from triggering `emitChanged`.

I compiled and built the software successfully on my local machine, and the application runs as expected with the changes I made.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a6aafda31269`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.