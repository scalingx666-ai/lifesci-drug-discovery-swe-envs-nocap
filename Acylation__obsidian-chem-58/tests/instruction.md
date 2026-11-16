# Issue

**Title:** Add options for explicit hydrogen

## Description

### Test cases
Check these cases with the config enabled/disabled to see the difference:
- Chiral center related: `N[C@@H](C)C(=O)O` & `N[C@H](C)C(=O)O`
- Explicit: `[H][O]C(=O)C(C)=CC1=CC=CC=C1`
- Implicit: `OC(=O)C(C)=CC1=CC=CC=C1`

### Explaination

The term `explicit hydrogen` is a little bit confusing. Here's a brief intro quoted from https://www.herongyang.com/Cheminformatics/SMILES-Hydrogen-Representations.html

> **How Hydrogens Are Represented in SMILES?** - Hydrogen are represented according to the following rules:
> 1. Explicitly as Atoms - A hydrogen can be represented by its atomic symbol in square brackets [H]. For example, [H][O][H] for water; [2H]O[2H] for heavy water; [H][H] for hydrogen molecule.
> 2. Explicitly as Counts - When hydrogens are connected to an atom, which is represented in square brackets, those hydrogens must be represented a count in the form of [xHn]. For example, "[OH2]" is the same as "O([H])[H]"
> 3. Implicitly - When hydrogens are connected to an atom, which is represented without square brackets, those hydrogens are implicitly represented according to normal valence assumptions. For example, "O" is the same as "O([H])[H]"

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2612039a9fce`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.