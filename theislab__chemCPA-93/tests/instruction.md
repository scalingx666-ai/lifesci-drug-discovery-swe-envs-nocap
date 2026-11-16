# Issue

**Title:** Add Chemical VAE

## Description

. This should be similar to the VAE presented in the original paper, but without jointly training the molecular property predictor. I didn't tune any hyperparameters, but the default HPs seem pretty tuned already.

I achieves pretty low KL div (should be well disentangled) and randomly sampling from the prior yields SMILES that are >95% valid, which is pretty impressive.

@MxMstrmn Can we schedule a few runs with this? I'd hope it's strictly better than the seq2seq model in every way.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f05947e985e0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.