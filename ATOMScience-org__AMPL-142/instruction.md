# Issue

**Title:** Bug dc261 restore

## Description

DeepChem changed the Multitask models over to Pytorch. As a result the DCNNModelWrapper can't wrap both the GraphConv (keras) and the Multitask (Pytorch) models anymore, because of the copy and saving functions. the DCNNModelWrapper is removed and split into 2 classes, GraphConvDCModelWrapper and MultitaskDCModelWrapper. These inherit the KerasDeepChemModelWrapper and PytorchDeepChemModelWrapper respectively.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6b9bf4c1807c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.