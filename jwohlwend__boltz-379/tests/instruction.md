# Issue

**Title:** Update mols.tar download logic

## Description

Related to #295 

The current logic for downloading the mols.tar archive at runtime goes like this:
1. Is there a folder named "mols" in the cache directory?
2. If not, download and extract mols.tar from HuggingFace

However, if you download the model weights from HuggingFace ahead of time but don't extract them, the existing logic wouldn't see a "mols" folder and try to download and extract the results. Why is this a problem? Because some HPC platforms allow users to download stuff from the internet ahead of time but not during a run. Some NextFlow environments (Like AWS HealthOmics) are like this. In those cases, you can reference external data dependencies which are "automagically" loaded into a working directory before the start of a run but not always extracted. You need to write some custom code to do so before calling `boltz predict`.

This PR updates the logic a bit to break apart the download and extract steps. So, the new logic looks like:
1. Is there a file named "mols.tar" in the cache director?
2. If not, download it.
3. Is there a folder named "mols" in the cache directory?
4. If not, extract mols.tar

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8b1627c9dc79`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.