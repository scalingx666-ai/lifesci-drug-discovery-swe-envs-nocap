# Issue

**Title:** Fixes error with several ring double bonds

## Description

This PR fixes some SMILES strings failing to be built e.g.

```python
>>> import autode as ade
>>> ade.Molecule(smiles=r'C1=C\N=C/C=N\C=C/C/1')
```
Raises a `LinAlgError`
```
...
    raise LinAlgError('%d-dimensional array given. Array must be '
numpy.linalg.LinAlgError: 1-dimensional array given. Array must be at least two-dimensional
```

Thanks to @TomWattsChem for spotting this. Seemingly this issue is limited to rings with several double bonds in

It also corrects a typo in `autode.exceptions.ReactionFormationFalied`.  Although this technically breaks backwards compatibility (`from autode.exceptions import ReactionFormationFalied` now raises an `ImportError`) I think it's very unlikely to be used outside of the internal package. Therefore, this PR remains for v1.1.2.

***

- [x] Rebase
- [x] Update changelog
- [x] Bump version
- [x] Fix typo (mentioned in #89)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ec957fa2be84`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.