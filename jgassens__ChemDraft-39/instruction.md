# Issue

**Title:** fix: native SMILES kekulizes aromatic bonds and reports unknown-order bonds

## Description

The native SMILES writer's bond-symbol helper wrote both `aromatic` and `unknown` orders as single, so a ring drawn with aromatic bonds exported as cyclohexane (C6H12) and an unknown bond silently became a definite single. Every path was affected: chain bonds, the general DFS writer and the single-ring fast path.

**Aromatic**: bonds are kekulized before writing. Carbons always take one double bond, O/S/Se never do, and N/P are decided by the search, which prefers the assignment leaving the most N–H: pyridine's N takes a double bond, pyrrole's keeps its hydrogen, imidazole gets exactly one N–H. A system with no Kekulé pattern is written single with a warning. Kekulé output was chosen over lowercase aromatic atoms because the app's valence model counts an aromatic bond as one slot and so cannot tell a pyridine N from a pyrrole N–H; a Kekulé string needs no such guess and both engines read it back exactly.

**Unknown**: written single with a warning. `~` was rejected: OpenChemLib reads `C~C` as an any-bond with no hydrogens (C2).

Warnings surface as `export.smiles_bond_order` in Copy As SMILES and the .smi/SDF export.

Tests reparse benzene, naphthalene, pyridine, pyrrole, imidazole, furan and thiophene through OpenChemLib, plus an unsolvable aromatic case and an unknown-order chain bond.

- `pnpm lint` clean; `pnpm vitest run`: 3299 passed.
- Build stamp bumped.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `52f77f38ae25`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.