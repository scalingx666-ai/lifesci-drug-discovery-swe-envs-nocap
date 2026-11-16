# Issue

**Title:** standard suite expansions

## Description

<!-- Thank you for your contribution! -->

## Description
standard suite support for ccsd gradients and ccsd(t) energies (except fc rohf - only validated for cfour -- psi4 is 10^-6 different). also lccd, lccsd, olccd ref values. also fixed an error handling bug in psiapi mode.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4c09a2389973`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.