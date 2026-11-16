# Issue

**Title:** Remove the adjacency cache from the VF matcher implementation.

## Description

Note the preferred matcher is now DF and not VF.

Fixes/Addresses #1319 by just removing the cache.

Here are some timing of SMARTS matches against ChEMBL 36 - the majority of the time is spent in aromaticity but the timings show the caching here just isn't worth. Furthermore the preferred sub-search algorithm is DF.

```
VF (+cache)	543678 hits	in 35.696 s	Cl
VF (-cache) 543678 hits	in 26.804 s	Cl
DF	        543678 hits	in 26.084 s	Cl

VF (+cache) 31181 hits	in 46.679 s	[aD3]a-!@a([aD3])[aD3]
VF (-cache)	31181 hits	in 46.679 s	[aD3]a-!@a([aD3])[aD3]
DF	        31181 hits	in 29.525 s	[aD3]a-!@a([aD3])[aD3]

VF (+cache) 2402409 hits	in 44.193 s	c1ccccc1
VF (-cache)	2402409 hits	in 43.072 s	c1ccccc1
DF	        2402409 hits	in 29.310 s	c1ccccc1

VF (+cache)	76 hits	in 39.318 s	O=C1CCc2ccc(OCCCCN3CCN(CC3)c3ccccc3)cc2N1
VF (-cache) 76 hits	in 39.246 s	O=C1CCc2ccc(OCCCCN3CCN(CC3)c3ccccc3)cc2N1
DF	        76 hits	in 27.189 s	O=C1CCc2ccc(OCCCCN3CCN(CC3)c3ccccc3)cc2N1
```

Note - QueryAtomContainer should probably be optimised and/or removed to provide the faster APIs like ``atom.getIndex()`` etc.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `df9ffdc42a9a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.