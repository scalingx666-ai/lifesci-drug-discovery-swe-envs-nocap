# Issue

**Title:** RAG Retriever: optional cross-encoder reranking (1.1.0)

## Description

FOR CONTRIBUTOR:
* [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [x] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [x] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

## What

Adds an optional reranker to the RAG Retriever (1.1.0). The tool takes 20 candidate chunks, scores each one against the question, and keeps the best Top K. Default is still "No reranking".

Two options:
- Hosted reranker from the LiteLLM proxy (`genai_models` rows with domain `rerank`, e.g. BGE-Reranker-v2-M3).
- Local HuggingFace cross-encoder (`huggingface` rows tagged `rag-reranker`, e.g. ms-marco-MiniLM-L6-v2, about 1 s per question on CPU).

Reranker settings are checked before the embedding step, so bad settings fail fast. No new container needed.

Also adds test data tables, so the existing data-table tests now really run the script.

## Tests

- `planemo test`: 5/5
- Extra checks in the tool container (35 cases) and manual runs in a local Galaxy.

## Results in Galaxy

Workflow: RAG Retriever, then LLM Hub (gemma-4-31b). bge-m3 embeddings, Top K 5, with and without the hosted reranker.

| scenario | right source ranked 1st | correct answers |
|---|---|---|
| 238 abstracts, 30 SciFact claims | 23 to **28** of 30 | 27 to 27 |
| one paper, 30 QASPER questions | 17 to 16 of 30 | 21 to 21 |

The reranker helps when there are many documents. For a single paper it makes no difference, because the tool splits a paper into only about 5 chunks.

@anuprulez could you have a look?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `345d61c75bf7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.