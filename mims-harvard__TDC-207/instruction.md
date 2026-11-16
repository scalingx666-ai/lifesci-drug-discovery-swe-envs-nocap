# Issue

**Title:** Improvements in the context of knowledge graph resources

## Description

Suggesting a new data function: **Knowledge Graph Mastery**, https://github.com/mims-harvard/TDC/discussions/23#discussioncomment-7364648

__Changes:__
- Add `knowledge_graph` module
- Introduce `KnowledgeGraph` python class
- Include `build_KG` function to enable creating graph from scratch
- Add `to_KG` method to current `primekg` in resource module to get `PrimeKG` as `KnowledgeGraph` object

__Features:__
- Generalized format to create, handle, and manipulate `KnowledgeGraph` datasets (mimiking the [PrimeKG](https://github.com/mims-harvard/PrimeKG) data frame)
- Enhance maintenance and data integration for future knowledge graphs , e.g.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0e14a64f6e9b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.