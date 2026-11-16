# Issue

**Title:** Add custom codecs for RDKit Molecules and Biotite AtomArrays

## Description

## Changelogs

- Add a custom object codec for RDKit Molecules and Biotite AtomArrays

---

_Checklist:_

- [ ] ~_Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [X] _Update the API documentation if a new function is added, or an existing one is deleted._
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

This PR builds on the discussion in #241. 

The use of custom `numcodecs`-compatible object codecs for use in Zarr seems like a natural interface point to document and implement conversion from and to drug discovery specific format. 

You would simply use this like: 

```py
import zarr
import datamol as dm
from polaris.dataset.zarr._codecs import RDKitMolCodec

root = zarr.open("test.zarr", mode="w")
root.empty("molecules", shape=100, dtype=object, object_codec=RDKitMolCodec(), chunks=(5,))
root["molecules"][0] = dm.to_mol("C1=CC=CC=C1")
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0df06a0ebe76`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.