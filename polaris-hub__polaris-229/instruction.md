# Issue

**Title:** chore: Optimize Zarr store copy operation to Hub storage

## Description

## Changelogs

- Implement a custom Zarr store copy operation in the `S3Store`

---

_Checklist:_

- [ ] ~_Was this PR discussed in an issue? It is recommended to first discuss a new feature into a GitHub issue before opening a PR._~
- [ ] ~_Add tests to cover the fixed bug(s) or the newly introduced feature(s) (if appropriate)._~
- [X] _Update the API documentation if a new function is added, or an existing one is deleted._
- [X] _Write concise and explanatory changelogs above._
- [X] _If possible, assign one of the following labels to the PR: `feature`, `fix`, `chore`, `documentation` or `test` (or ask a maintainer to do it for you)._

---

A recent dataset added to the Hub sported a Zarr archive of modest size, but with a large number of files (194.056 MiB, 5067 files). The large number of files and the overhead of copying them to the Hub storage resulted in a transfer time of over 30 minutes. For comparison, using [Rclone](https://rclone.org/) to transfer the same Zarr archive to the same storage backend required 7 minutes.

The root cause of the client's slow upload lies in the implementation of the [`zarr.copy_store`](https://zarr.readthedocs.io/en/stable/api/convenience.html#zarr.convenience.copy_store) we use in our `StorageSession` class. This implementation makes no assumption about the nature of the source or destination stores, so it uses the most basic API supported by a Zarr store, [`MutableMapping`](https://docs.python.org/3/library/collections.abc.html#collections.abc.MutableMapping). It sequentially iterates through every key in the source store, checks their presence in the destination store, and then adds them to that store.

This PR updates our `S3Store` implementation with a custom copy method, that can leverage more efficient S3 operations, as well as parallel and concurrent operations, to improve throughput. The above mentioned dataset can now be copied to the Hub storage in ~2 minutes.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9e1a68b72adc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.