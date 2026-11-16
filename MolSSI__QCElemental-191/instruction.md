# Issue

**Title:** reduced mol storage 2

## Description

<!-- Thank you for your contribution! -->

## Description
Continuation of #190 with all fields targeted. This is strictly test driven dev on existing test suite. All pass but 3 and those are ok if turn off default filtering. The 3 that don't pass I don't understand b/c masses are perfectly accessible (https://github.com/MolSSI/QCElemental/compare/master...loriab:smollmol2?expand=1#diff-c1df0b88317a0c0331bea59a1793059cR769) but not getting stashed for hashing.

```
[ 1.00782503223 15.99491461957 15.99491461957  1.00782503223]
superdict
schema_name qcschema_molecule
schema_version 2
validated True
symbols ['H' 'O' 'O' 'H']
geometry [[ 1.7317  1.2909  1.0371]
 [ 1.3156 -0.0074 -0.2807]
 [-1.3143  0.0084 -0.2741]
 [-1.7241 -1.3079  1.0277]]
name H2O2
identifiers None
comment None
molecular_charge 0.0
molecular_multiplicity 1
masses None
real None
atom_labels None
atomic_numbers None
mass_numbers None
connectivity None
fragments None
fragment_charges None
fragment_multiplicities None
fix_com False
fix_orientation False
fix_symmetry None
provenance {'creator': 'QCElemental', 'version': 'v0.12.0+59.gce318ac', 'routine': 'qcelemental.molparse.from_schema'}
id None
extras None
symbols ['H' 'O' 'O' 'H']
masses None
```

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `55e3102fe440`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.