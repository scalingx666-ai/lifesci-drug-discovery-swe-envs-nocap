# Issue

**Title:** Add LiteLLM embedding model support to RAG retriever

## Description

This PR adds support for LiteLLM-hosted embedding models to the RAG Retriever tool, reusing the genai_models configuration from LLM Hub. The version suffix has also been bumped to 2.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e9499d2b979c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.