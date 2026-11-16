# Issue

**Title:** request to add a mol2 file reader

## Description

Hello!

My laboratory deals with a lot of multi-mol2 files.
So adding a function that reads in a multi-mol2 file would be super helpful!
I have created a feature that reads in the mol2 file and be able to return a list of rdkit objects so it can be worked on ASAP.

NOTE: In the RDKIT docs, the `rdmolfiles.MolFromMol2Block` and `rdmolfiles.MolFromMol2File` are strongly compatible with mol2 data that has CORINA atom types. ([more info](https://www.rdkit.org/docs/source/rdkit.Chem.rdmolfiles.html))

Further, `rdmolfiles.MolFromMol2File` is definitely exist to take in a Mol2 file, but for some reason they only process
the first molecule, which is weird. So that is why I added some logic to process multiple molecules.

Thank You,
Steven Pak

btw, great repo! It definitely easier to process molecules!

Checklist:
- [x] Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate).
- [ ] Update the API documentation is a new function is added or an existing one is deleted.
- [x] Added a `news` entry.
  - _copy `news/TEMPLATE.rst` to `news/my-feature-or-branch.rst`) and edit it._

---

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a923213a1c34`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.