# Issue

**Title:** Expose chemenv attributes and misc cli, featurizer enhancements

## Description

# Changes

1. Expose ICOHPList, charges and CompleteCohp objects as Analysis class properties
2. Make possible to switch charges used for LobsterNeighbours to Loewdin, Mulliken or Valences
3. Add option in cli to switch charges in analysis
4. Enabling switching analysis type in FeaturizeLobsterpy to COOP / COBIs

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `70bd797fc362`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.