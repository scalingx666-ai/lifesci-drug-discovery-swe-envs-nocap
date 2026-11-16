# Issue

**Title:** Use Fulqrum's sci_solver factory in the integration guide (backport #427)

## Description

~~Depends on qiskit-community/fulqrum#140, which proposes `fulqrum.addon_sqd_support`. Opening as a draft to show what the guide looks like if that PR lands.~~ Qiskit/fulqrum#140 merged and shipped in fulqrum 0.5.0.

The guide currently builds its `sci_solver` inline, and then repeats nearly all of it for the PRIMME example, where the only difference is which eigensolver is called. With the factory, each becomes a single call:

```python
sci_solver = sci_solver_from_integrals(hcore, eri, tol=1e-12)
```

and the PRIMME variant is one more argument:

```python
sci_solver = sci_solver_from_integrals(hcore, eri, eigensolver=primme.eigsh, tol=1e-12)
```

That removes 116 lines and adds 18.

The code this removes is the easiest to get wrong. Fulqrum orders a subspace with the beta half string major, so the eigenvector needed transposing, and `fq.Subspace` sorts each list of half strings, so the unpacking depended on the CI strings arriving sorted. Getting either wrong leaves the energy correct while attaching amplitudes to the wrong determinants, which then corrupts the next configuration-recovery iteration. #423 documents the sortedness half of that as a guarantee of `diagonalize_fermionic_hamiltonian`.

~~This also raises the `fulqrum` extra's floor to 0.5.0, the version that would carry the module. That release does not exist yet.~~ See the update below: the floor stays at 0.4.4 on this stable branch.

## Verification

I ran the old inline solver and the factory with the same seed at the guide's own problem size (N2/6-31g, `norb=16`, 5 batches, 5 iterations). They agree exactly:

- energy `-109.034026675594` both ways
- identical amplitude shape `(808, 808)`
- zero difference in amplitudes and occupancies

The notebook also executes end to end against the Fulqrum branch, in about 2 minutes 41 seconds, and `nbqa ruff` passes.

<hr>
This pull request was drafted by Claude Opus 5 under my guidance.
<hr>This is an automatic backport of pull request #427 done by [Mergify](https://mergify.com).

## Update: keeping the `fulqrum` floor at 0.4.4

The backport as Mergify created it raised the `fulqrum` extra's floor from 0.4.4 to 0.5.0, inheriting that from #427. That is inappropriate on a stable branch: it would break environments that already satisfy the declared 0.4.4 bound.

9d10860 reverts the floor and skips the guide in the minimum-version job instead, which is the job that actually fails. That job pins every dependency to the declared floor, so it installs fulqrum 0.4.4, where `fulqrum.addon_sqd_support` does not exist and the notebook fails on import. The latest- and development-version workflows install the current fulqrum and keep executing the notebook, so the guide stays covered there.

`tox.ini` already interpolates `{posargs}` into the notebook environment's pytest call ahead of `docs/`, so the exclusion is a tox argument and no shared configuration changes:

```
tox -e py,notebook -- --ignore=docs/guides/integrate_fulqrum.ipynb
```

That takes the collected notebooks from 8 to 7, dropping only this guide. The commit also removes the "Cap notebook memory for CI" step from this one job, since `integrate_fulqrum.ipynb` was its only target; the script and the step remain in the other two workflows.

The tradeoff: on `stable/0.14` this guide is no longer executed at the minimum versions. That is inherent to backporting a guide that depends on a newer optional dependency.

<hr>
This update was drafted by Claude Opus 5 under my guidance.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3f4e699e3fa5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.