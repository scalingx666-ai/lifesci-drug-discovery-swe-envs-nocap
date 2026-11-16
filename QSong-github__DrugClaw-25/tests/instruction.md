# Issue

**Title:** fix: propagate entity fields in retrieved_content view; add improved …

## Description

…audit script

agent_retriever.py: _evidence_items_to_retrieved_content was hardcoding source_entity, target_entity, target_type as empty strings and using item.claim (a full NL sentence) as relationship. All four values already exist in item.metadata (populated by build_evidence_items_for_skill in evidence.py) — this commit reads them from there. Document-type skills that never set these fields in their records continue to produce empty strings; relational skills (ChEMBL, SIDER, DDInter, RepoDB, etc.) will now correctly surface their entity and relationship data in this view.

entity_audit.py (new): three-mode CLI (single / matrix / all) that audits the full evidence layer. Key improvements over the previous ad-hoc script:
  - Reads correct EvidenceItem fields (source_skill, structured_payload, metadata.source_entity / target_entity)
  - Absent-skill detection: diffs requested skills vs. skills with evidence items, then pulls retrieval_diagnostics for error/strategy
  - Per-skill native-key validation using a curated SKILL_EXPECTED_KEYS dict (ChEMBL → chembl_id/target_chembl_id, SIDER → side_effect_name, DDInter → drug1_name/drug2_name, RepoDB → drug_name/ind_name, etc.)
  - DOCUMENT_SKILLS whitelist suppresses false-positive entity warnings for label/review/NLP-type skills where empty entities are by design
  - Writes per-probe JSON + summary_matrix.tsv for regression baselining

https://claude.ai/code/session_01DbDWTryjCk72B4bZJBr6rw

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7bcce68af902`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.