# Issue

**Title:** Add DNA Foundation Models

## Description

This PR adds a new Galaxy tool, **DNA Foundation Models**, integrating the DNABERT-2 foundation model into Galaxy.

The tool supports two main execution modes:

* **Embedding mode**: generates sequence embeddings from FASTA input
* **Fine-tuning mode**: trains or adapts models using tabular datasets, with support for both full fine-tuning and LoRA-based parameter-efficient tuning

In embedding mode, the tool processes a FASTA file by batching sequences through the model to generate embeddings. Pooling is configurable (`CLS`, mean, or max), and outputs are written as a tabular file. Optionally, attention visualizations can be enabled, producing additional outputs via BertViz and related utilities.

In fine-tuning mode, the tool takes tabular datasets (train/dev/test) in `(sequence, label)` format and passes training parameters directly to the underlying training script. It exposes the main Trainer configuration options, such as batch size, learning rate, number of epochs, evaluation steps, and logging frequency.

Two training strategies are supported:

* Full fine-tuning
* LoRA-based fine-tuning (optionally enabled, with configurable rank, alpha, dropout, and target modules)

Training artifacts (evaluation metrics, predictions, trainer state) are returned as outputs. Optionally, the trained model is returned as a `.tar.gz` archive.

### Notes

The original DNABERT-2 model is based on a MosaicBERT architecture that relies on a version of Flash Attention not compatible with newer PyTorch releases. This tool instead uses model weights loaded through an updated MosaicBERT implementation to ensure compatibility.

The model can be retrieved using the following script:
[model-retrieval.py](https://github.com/user-attachments/files/31384995/model-retrieval.py)

FOR CONTRIBUTOR:
* [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [x] License permits unrestricted use (educational + commercial)
* [x] This PR adds a new tool or tool collection
* [ ] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

There are two labels that allow to ignore specific (false positive) tool linter errors:

* `skip-version-check`: Use it if only a subset of the tools has been updated in a suite.
* `skip-url-check`: Use it if github CI sees 403 errors, but the URLs work.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `183ed5e92151`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.