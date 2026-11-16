# Issue

**Title:** psithon and psiapi

## Description

<!-- Thank you for your contribution! -->

## Description
~Adapt psi harness to choose psithon or psiapi for `found` and `version` fns. What I'm aiming for is to not require PATH _and_ PYTHONPATH environment edits to run psi4 (which calls qcng which calls psi4) when providing full path to exe.~

If psi4 is found through PATH _or_ PYTHONPATH, this sets the env in qcng to make both psithon and psiapi available.
- does not check if you had PATH pointing to one psi4 installation and PYTHONPATH to another. just don't do that.
- running in psiapi when psi4 in PATH only works for latest ddd branch b/c I had to add `psi --module` to access that importdir.
- result of this is that running tests in ddd no longer requires typing path to `bin/psi4` _and_ having PATH set _and_ having PYTHONPATH set. hoping this will avert lots of questions down the road.

wrt #213, the `found()` fn universally means fully operational, so let's keep that meaning and add extra checks for harness-dep programs into the found. For the setup guidance, let's just stop the generic "cannot be found" and instead propagate `found`'s nice messages and also link how to run `found` in the `qcengine info` page.

## Questions
- [ ] ~This PR works for my purposes except I have to hack around "psi4 is registered with QCEngine, but cannot be found." b/c psiapi vs psithon as a mode of operation (usually supplied in `AtomicInput`) isn't know at that stage. Any strong opinions on whether psithon and psiapi should be set up as separate harnesses based on whether PATH or PYTHONPATH had been provided by the user. An alternative is that both psithon and psiapi modes can be made available from one of PATH/PYTHONPATH so that `found` could look for both and figure out the mods to `env` that need to be passed to `popen`.~

## Changelog description
included

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e370e8621956`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.