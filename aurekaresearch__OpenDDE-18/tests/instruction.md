# Issue

**Title:** fix ion feature metadata

## Description

## Summary

* Fix ion-containing inference inputs, such as protein + Zn, when MSA or template features are enabled.
* Preserve ion entities in the asymmetric-chain metadata used for feature-coordinate mapping.
* Prevent `map_to_standard()` failures caused by missing or shifted ion chain metadata.

## Root cause

* The general input parser supported `ion` entities, but the inference MSA and template featurizers only constructed metadata for proteins, nucleic acids, and ligands.
* Ion entities therefore did not advance the asymmetric-chain index or receive placeholder sequence metadata.
* This caused missing or shifted asymmetric-chain IDs when mapping complete atom/token representations into MSA and template coordinates.

## Changes

* Add explicit `ion` handling to `InferenceMSAFeaturizer`.
* Add equivalent `ion` handling to `InferenceTemplateFeaturizer`.
* Treat ions as non-polymer entities while preserving the existing ligand path.
* Generate the placeholder sequence independently for each ion copy from its centre-atom count.
* Correctly advance asymmetric-chain indexing for single ions, multiple ion copies, and separate ion entities.
* Keep the implementation generic for supported ions rather than special-casing Zn.

## Test coverage

* Add CPU regression tests for both MSA and template feature construction.
* Cover protein followed by an ion.
* Cover an ion followed by protein.
* Cover an ion entity with `count: 2`.
* Cover protein + ligand + ion inputs.
* Cover multiple independent ion entities.
* Cover an ion positioned between two protein entities.
* Verify that MSA, profile, and template feature dimensions match the complete atom/token representation.

## Validation

* Confirmed that the regression tests reproduce the original asymmetric-chain mapping failure before the fix.
* Confirmed that the focused ion metadata tests pass after the fix.
* Confirmed that the full CPU test suite passes.
* Confirmed successful GPU inference for a protein + Zn input with MSA enabled.
* Confirmed that the resulting structure and confidence outputs are generated with valid indexing.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f607bb3c9ff2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.