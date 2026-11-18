# Issue

**Title:** Rag tool

## Description

FOR CONTRIBUTOR:
* [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [x] License permits unrestricted use (educational + commercial)
* [x] This PR adds a new tool or tool collection
* [ ] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

---

## Description

This PR adds a new Galaxy tool: **RAG Retriever**.

The tool performs document retrieval for Retrieval-Augmented Generation (RAG) workflows using LlamaIndex and HuggingFace sentence-transformers embeddings. It extracts the most relevant text chunks from input documents based on semantic similarity to a user query.

The output is a context file that can be used as input for downstream LLM tools.

---

## Example Workflow

This tool is intended to be used together with the **LLM Hub** tool.

Typical workflow:

1. Upload one or more documents (PDF, JSON, TXT, CSV, Markdown, etc.)
2. Upload an embedding model archive (`.tar.gz` / `.tgz`) containing a HuggingFace sentence-transformers model
3. Run **RAG Retriever** to extract relevant context chunks
4. Pass the generated `rag_context.txt` file to the **LLM Hub** tool
5. Ask a question using the retrieved context

Pipeline overview:

Documents + Embedding Model Archive + Question → RAG Retriever → Context → LLM Hub → Answer

**Example Galaxy workflow combining RAG Retriever and LLM Hub:**

![Galaxy workflow](https://github.com/user-attachments/assets/13ef70a5-25b8-4fc8-ab37-441bb8d872ce)

## Notes

- The tool does not generate answers itself, but prepares high-quality context for LLMs.
- Supports multiple input formats including PDF, JSON, TXT, CSV, and Markdown.
- Accepts a HuggingFace sentence-transformers embedding model as a `.tar.gz` / `.tgz` archive input.
- The archive-based model input preserves the original model directory structure required for loading custom embedding models.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3466073da870`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.