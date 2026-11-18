# Issue

**Title:** Fix RAG Retriever crash on markdown files

## Description

* [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [x] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [x] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

Fix `Unsupported file type: markdown` error. The XML declares `format="markdown"` but `valid_file_types` checked for `"md"`. Bump galaxy version suffix 0 → 1.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e160e1cea4d7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.