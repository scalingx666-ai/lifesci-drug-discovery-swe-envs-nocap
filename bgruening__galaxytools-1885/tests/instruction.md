# Issue

**Title:** Add 3Dtrees: Metadata

## Description

## What's new

Adds the `3dtrees_metadata` Galaxy wrapper, Tool Shed metadata, and focused
test data.

The wrapper runs the 3Dtrees metadata container and extracts administrative
GADM attributes plus WWF Terrestrial Ecoregions v2.0 attributes from a
`collection_summary.json` centroid. It also supports a LAS/LAZ header bounds
fallback when no centroid or collection geometry is available.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `98179300a743`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.