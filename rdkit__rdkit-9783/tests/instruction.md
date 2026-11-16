# Issue

**Title:** Fix H-bond acceptor definitions for N atoms in BaseFeatures.fdef

## Description

.

### Description
In `Data/BaseFeatures.fdef`, `NAcceptor` is defined across multiple lines:
- line 19: `AtomType NAcceptor [n;+0;!X3;!$([n;H1](cc)cc)]`
- line 20: `AtomType NAcceptor [$([N;H0]#[C&v4])]`
- line 22: `AtomType NAcceptor [N&v3;H0;$(Nc)]`

When `FeatureParser.cpp` processes multiple `AtomType` entries for the same label, it concatenates them with commas inside brackets (`[<def1>,<def2>,<def3>]`).
In SMARTS syntax, the semicolon `;` represents low-precedence AND, while `,` represents OR. Because line 19 used `;`, the semicolon bound across `,` across all alternatives. As a consequence, the entire pattern required `n` (aromatic nitrogen) for every alternative, silently preventing non-aromatic nitrogens (like nitrile `[$([N;H0]#[C&v4])]` and tertiary aniline nitrogens) from matching.

### Solution
- Replace low-precedence `;` with high-precedence `&` in the `NAcceptor` definitions in `Data/BaseFeatures.fdef`:
  - `AtomType NAcceptor [n&+0&!X3&!$([n&H1](cc)cc)]`
  - `AtomType NAcceptor [N&v3&H0&$(Nc)]`
  This matches the convention already used for `NDonor` in line 5.
- Add regression test `testGithub9770` in `Code/GraphMol/MolChemicalFeatures/Wrap/testChemicalFeatures.py` verifying that:
  - Acetonitrile (`CC#N`) matches 1 H-bond acceptor on the nitrile N (previously matched 0).
  - Benzonitrile (`c1ccccc1C#N`) matches 1 H-bond acceptor on the nitrile N (previously matched 0).
  - Tertiary aniline (`CN(C)c1ccccc1`) matches 1 H-bond acceptor.
  - Pyridine (`c1ncccc1`) retains 1 H-bond acceptor.
  - Indole (`c1ccc2[nH]ccc2c1`) retains 0 H-bond acceptors.

### Verification
Ran test suite covering feature definition parsing:
- `testChemicalFeatures.py`: 10/10 tests passed (including `testGithub9770`).
- `UnitTestFeatFinderCLI.py`: 2/2 tests passed.
- `UnitTestPharmacophore.py`: 4/4 tests passed.
- `UnitTestMatcher.py`: 4/4 tests passed.
- `UnitTestSignature.py`: 10/10 tests passed.

Drafted with Claude / Reviewed and verified by Davis Rens.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f7d30a8eb1d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.