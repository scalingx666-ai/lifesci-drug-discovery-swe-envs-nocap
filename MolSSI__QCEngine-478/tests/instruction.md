# Issue

**Title:** Fix psi4 + rdkit on Windows

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
Psi4+windows+MKL is known to be a little flaky wrt MKL versions (2024.2.2 bad), but that's build into `psi4=1.9.1=*_10`. This PR fixes a new problem that affects the same tests (~50 fail; first shows up ~38% with ghost_tricky; Linalg does not converge iirc). It seems to be entirely with the latest rdkit version, where the only difference btwn working and broken envs is below.

```
> diff env_pass env_fail
...
librdkit                     2025.03.4              h0cb3073_0       |	librdkit                     2025.03.5              h0cb3073_0      
rdkit                        2025.03.4              py311h45ae9fe_0  |	rdkit                        2025.03.5              py311h45ae9fe_0 
```

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [ ] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1d2762c4687f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.