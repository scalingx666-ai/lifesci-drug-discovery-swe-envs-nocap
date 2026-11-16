# Issue

**Title:** protocol for retaining DSL files

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
So the usual qcng philosophy is to collect stdout and any useful output files from a run (e.g., cfour's `GRD` and gamess's dat file) and process them (perhaps even rotating coordinates) into `AtomicResult` fields, then ditch the files. Whether stdout gets returned depends on the `protocols.stdout` and the files are dropped (except that I sometimes stash them in extras). However, folks like to see their files, esp. since they may be far more familiar with native file formats than with QCSchema format. Since we're more of a bring-everything-back rather than inspect-the-scratch-dir shop, it might be nice to let files be seen. Even if you're willing to abandon all output files, I'll throw in that the whole harness-composed input for a gamess run _is not available_ from the stdout, nor can it be forcibly made to be, so adding it to the AtomicResult is almost necessary to fully replicate the job.

Standard way to influence the layout of a model is with a protocol, so here's an untested proposition. Ideas for naming the field include "ancillary", "dsl", "native", "stdfiles". Thoughts on this?

ADDED: "vulgate", "vernacular", "auxilliary"

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5e556c8b8107`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.