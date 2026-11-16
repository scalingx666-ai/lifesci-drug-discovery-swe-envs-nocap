# Issue

**Title:** Speed up and reduce memory usage of fused ring system detection in Kekulize

## Description

#### Reference Issue

Found while investigating #9756

#### What does this implement/fix? Explain your changes.

With the new ring finder `Kekulize` and `Compute2DCoords` group rings into fused systems by comparing every pair of rings, so time and memory grows with the square of the ring count.

This PR adds `RingUtils::findFusedRingSystems` which finds the same groups without having to compare every ring pair, and uses it in `Kekulize` and `Compute2DCoords` while keeping the output unchanged.

I asked Claude to benchmark this for me: For [12]cycloparaphenylene (4,108 rings), `Kekulize` goes from **5.1 s to 4 ms** and from **217 MiB to 5 MiB** peak memory (not the log axis).

<img width="1500" height="570" alt="fused_ring_systems" src="https://github.com/user-attachments/assets/8385ac04-1e5a-4a56-83bd-6db4826926c7" />

@ricrogz let me know if you see any issues with this.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `78cb05c3db00`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.