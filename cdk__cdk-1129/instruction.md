# Issue

**Title:** fix crash in SmilesGenerator when calling with reaction not having one or more reaction components

## Description

Without the change in `SmilesGenerator::String create(IReaction,int[])` the test method `EmptyReactionSmilesGenerationTest.java::emptyReactionInstance_smilesFlavorCanonicalStereo_test` fails.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8fb4e8c529d4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.