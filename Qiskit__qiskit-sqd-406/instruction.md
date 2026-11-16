# Issue

**Title:** Fix unresolved cross-references found by Sphinx nitpicky mode

## Description

Building the docs with `nitpicky = True` locally turns up eight unresolved references in three groups. None of them fail the build today, because nitpicky is off, but each one is a link that silently renders as plain text.

### An API reference page for `qiskit_addon_sqd.processes`

The module is public and the [HPC acceleration guide](docs/guides/hpc_acceleration.rst) describes its concepts, but it had no page. The `:func:` references to `processes.broadcast` and `processes.barrier` in the `fermion` docstrings therefore had nothing to resolve to. This is the one substantive gap of the three — the module's documentation was simply not being built.

### `scipy` added to `intersphinx_mapping`

`project_operator_to_subspace` is annotated as returning `spmatrix`, which could not resolve without it. scipy's inventory carries `scipy.sparse._matrix.spmatrix` as an alias, so the return type now links to the public `spmatrix` page.

### Two release notes referencing removed functions

`flip_orbital_occupancies` (removed in 0.10) and `bitstring_matrix_to_sorted_addresses` (deprecated in 0.6, since removed) were still written with the `:func:` role. Only those two dead names become literals; the notes' wording is unchanged, and cross-references to functions that still exist are left alone.

### Why nitpicky is not enabled here

I ran it as a one-off audit rather than turning it on, because 155 references in these docs resolve only through a remote inventory — 142 of them through numpy, which supplies every `np.ndarray` annotation. A reorganized upstream docs URL would become 142 CI errors on a commit that changed nothing.

The protection it would add is also largely redundant. Since the build already runs with `-W`, an unreachable inventory fails CI with a single clear "failed to reach any of the inventories" warning, which is easier to diagnose than the pile of "target not found" errors nitpicky would produce from the same cause. I'm open to revisiting it as a separate non-blocking job if that seems worthwhile.

<hr>

This pull request was drafted by Claude Opus 5 under my guidance.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0cd51110949e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.