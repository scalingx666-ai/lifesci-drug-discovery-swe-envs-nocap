# Issue

**Title:** ChemDraw CDX: handle additional aromatic/fractional bond-order codes

## Description

`ChemDrawBinaryXFormat::DoFragmentImpl` mapped only CDX bond-order value `0x0080` to an aromatic bond (order 5); the other fractional/aromatic codes fell through to the default and were read as single bonds.

This adds the remaining aromatic/fractional CDX bond-order codes:

```
0x0040  // aromatic (0.5)
0x0080  // aromatic (1.5)   [existing]
0x0100  // aromatic (2.5)
0x0081  // single + 1.5
0x0082  // double + 1.5
0x0101  // single + 2.5
0x0102  // double + 2.5
```

all mapped to order 5 (aromatic), so molecules drawn in ChemDraw with these bond annotations import with correct aromaticity instead of as single bonds.

I'm happy to add a small `.cdx` round-trip test to the suite if that would help.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `54e394ddaf7b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.