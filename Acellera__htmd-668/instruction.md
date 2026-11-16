# Issue

**Title:** condensed the element guess warning

## Description

I got sick of screens full of mol2 warnings so I condensed this:

```
2018-04-26 12:33:34,594 - htmd.molecule.readers - WARNING - Element of atom ID 1 could not be automatically guessed from its MOL2 atomtype (ca).
2018-04-26 12:33:34,594 - htmd.molecule.readers - WARNING - Element of atom ID 2 could not be automatically guessed from its MOL2 atomtype (za).
2018-04-26 12:33:34,594 - htmd.molecule.readers - WARNING - Element of atom ID 3 could not be automatically guessed from its MOL2 atomtype (zb).
2018-04-26 12:33:34,594 - htmd.molecule.readers - WARNING - Element of atom ID 4 could not be automatically guessed from its MOL2 atomtype (ca).
2018-04-26 12:33:34,594 - htmd.molecule.readers - WARNING - Element of atom ID 5 could not be automatically guessed from its MOL2 atomtype (ca).
2018-04-26 12:33:34,595 - htmd.molecule.readers - WARNING - Element of atom ID 6 could not be automatically guessed from its MOL2 atomtype (zb).
2018-04-26 12:33:34,595 - htmd.molecule.readers - WARNING - Element of atom ID 7 could not be automatically guessed from its MOL2 atomtype (za).
2018-04-26 12:33:34,595 - htmd.molecule.readers - WARNING - Element of atom ID 8 could not be automatically guessed from its MOL2 atomtype (ca).
2018-04-26 12:33:34,595 - htmd.molecule.readers - WARNING - Element of atom ID 9 could not be automatically guessed from its MOL2 atomtype (ca).
2018-04-26 12:33:34,595 - htmd.molecule.readers - WARNING - Element of atom ID 10 could not be automatically guessed from its MOL2 atomtype (nb).
2018-04-26 12:33:34,595 - htmd.molecule.readers - WARNING - Element of atom ID 11 could not be automatically guessed from its MOL2 atomtype (ca).
2018-04-26 12:33:34,595 - htmd.molecule.readers - WARNING - Element of atom ID 12 could not be automatically guessed from its MOL2 atomtype (ca).
2018-04-26 12:33:34,595 - htmd.molecule.readers - WARNING - Element of atom ID 13 could not be automatically guessed from its MOL2 atomtype (ca).
2018-04-26 12:33:34,595 - htmd.molecule.readers - WARNING - Element of atom ID 14 could not be automatically guessed from its MOL2 atomtype (ca).
2018-04-26 12:33:34,595 - htmd.molecule.readers - WARNING - Element of atom ID 15 could not be automatically guessed from its MOL2 atomtype (zc).
2018-04-26 12:33:34,595 - htmd.molecule.readers - WARNING - Element of atom ID 16 could not be automatically guessed from its MOL2 atomtype (zc).
2018-04-26 12:33:34,595 - htmd.molecule.readers - WARNING - Element of atom ID 17 could not be automatically guessed from its MOL2 atomtype (ha).
2018-04-26 12:33:34,595 - htmd.molecule.readers - WARNING - Element of atom ID 18 could not be automatically guessed from its MOL2 atomtype (ha).
2018-04-26 12:33:34,595 - htmd.molecule.readers - WARNING - Element of atom ID 19 could not be automatically guessed from its MOL2 atomtype (ha).
2018-04-26 12:33:34,595 - htmd.molecule.readers - WARNING - Element of atom ID 20 could not be automatically guessed from its MOL2 atomtype (ha).
2018-04-26 12:33:34,595 - htmd.molecule.readers - WARNING - Element of atom ID 21 could not be automatically guessed from its MOL2 atomtype (ha).
2018-04-26 12:33:34,595 - htmd.molecule.readers - WARNING - Element of atom ID 22 could not be automatically guessed from its MOL2 atomtype (ha).
2018-04-26 12:33:34,595 - htmd.molecule.readers - WARNING - Element of atom ID 23 could not be automatically guessed from its MOL2 atomtype (ha).
2018-04-26 12:33:34,595 - htmd.molecule.readers - WARNING - Element of atom ID 24 could not be automatically guessed from its MOL2 atomtype (zd).
2018-04-26 12:33:34,595 - htmd.molecule.readers - WARNING - Element of atom ID 25 could not be automatically guessed from its MOL2 atomtype (zd).
2018-04-26 12:33:34,595 - htmd.molecule.readers - WARNING - Element of atom ID 26 could not be automatically guessed from its MOL2 atomtype (zd).
2018-04-26 12:33:34,595 - htmd.molecule.readers - WARNING - Element of atom ID 27 could not be automatically guessed from its MOL2 atomtype (zd).
```

to this
```
2018-04-26 12:40:54,936 - htmd.molecule.readers - WARNING - Could not guess elements for 27 atoms with MOL2 atomtypes (ca, ha, nb, za, zb, zc, zd).
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e5f49ad88748`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.