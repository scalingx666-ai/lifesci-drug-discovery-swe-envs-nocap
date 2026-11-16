# Issue

**Title:** Feature: Download for V2 datasets

## Description

## Changelogs

- Added support for downloading V2 Datasets from the Hub.
- Given that `authlib >1.3.0` is [not yet available for Conda](https://github.com/conda-forge/authlib-feedstock), we can't assume a  is available and needed some code to handle the case that `token` is None in `ensure_active_token()`.
- Excluded some fields from the `repr_dict` to prevent excessive compute when visualizing the dataset.

---

_Checklist:_

- [X] _Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [X] _Update the API documentation if a new function is added, or an existing one is deleted._
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

The `client.get_dataset()` tries loading a V1 dataset first, and then the V2 if a 404 is raised. This adds some overhead, but given the deadline I would like us to optimize this later. 

### A word on testing

We don't have a great way setup yet to test these changes, so I manually created three datasets on the `cas` Neon branch: 

1. A vanilla V1 dataset
2. A V1 dataset with pointer columns
3. A V2 dataset

All three of these datasets are public, so as long as you use my Neon branch you should be able to replicate the tests I've done using this code:
```python
with PolarisHubClient(settings=settings) as client:
    # V2 dataset
    dataset = client.get_dataset(owner="casw3", name="BELKA-v5")
    print(dataset[123456])

    # V1 dataset with pointers
    dataset = client.get_dataset(owner="casw3", name="v1-with-pointers-2")
    print(dataset[0])

    # Vanilla V1 dataset
    dataset = client.get_dataset(owner="casw3", name="biogen-adme-v1")
    print(dataset[123])
```

This also works:
```py
for name in ["BELKA-v5", "v1-with-pointers-2", "biogen-adme-v1"]:
    po.load_dataset(f"casw3/{name}")
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b6092bcb3bfe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.