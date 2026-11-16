# Issue

**Title:** tools: update 3dtrees smart tile to v2.2

## Description

## Summary
- update the 3DTrees SmartTile Galaxy wrapper to version 2.2+galaxy15
- use the published Docker image ghcr.io/3dtrees-earth/3dtrees_smart_tile:v2.2
- wire fixed file-level workers with GALAXY_SLOTS-backed spatial chunks
- keep prod-merged outputs opt-in and support tree sidecar inputs

## Validation
- python -m xml.etree.ElementTree tools/3dtrees_smart_tile/smart_tile.xml
- planemo lint tools/3dtrees_smart_tile/smart_tile.xml

Note: planemo lint exits 0; the local environment prints an optional h5py/numpy assertion-module warning before lint output.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `afa017473440`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.