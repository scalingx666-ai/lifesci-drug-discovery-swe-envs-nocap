# Issue

**Title:** New sampling strategy for mini-batch diversification

## Description

This PR integrates the improvement suggested by the paper [Diverse Mini-Batch Selection in Reinforcement Learning for Efficient Chemical Exploration in de novo Drug Design](https://arxiv.org/abs/2506.21158). It provides a sampling strategy `dpp` that enhances the chemical diversity of `multinomial` sampling. The paper focuses on the Reinvent model, but the strategy is model-agnostic and, therefore, I have also implemented this sample strategy for the other models (except Pepinvent). It can be implemented for Pepinvent, but then we need to select an appropriate similarity function between peptides.

# Key Changes

## Core implementation:
* Adds a sampling strategy `dpp` for the Reinvent, Linkinvent, Libinvent and Mol2mol samplers.
* No changes of the model-specific sampling, the PR uses the models' multinomial sampling with oversampling to select a diverse mini-batch.
* Allows specifying `sample_strategy` in TOML config file for all models. If no sample strategy is given, `None` is still the default for non-Transformer models for backward compatibility.

## Testing:
* Add sampling tests (integration tests) for the dpp-based samplers of reinvent, linkinvent, libinvent and mol2mol.
* All tests pass.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c2fd46bd7276`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.