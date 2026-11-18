# Build notes - Drug Discovery & Cheminformatics

Repo2RLEnv pr_diff (v0.9.6), Harbor-format output. Domain: drug-discovery.

## Funnel

| Stage | Count |
|---|---|
| Domain candidates (deduped) | 498 |
| After active+star+noise filter | 272 |
| Final target list (cap unlimited) | 272 |
| Repos with >=1 task | 163 |
| Repos with 0 tasks | 44 |
| Total tasks (unlimited (no per-repo cap)) | 8346 |

## Generation

- Shared task bank: each repo generated once (pr_diff, limit=3,
  max_files_per_pr=15, min_loc_changed=2), 4-way concurrency,
  rate-limit-aware with .done checkpoint resume.
- Per-domain consolidation: rank by reward_calibration.loc_changed desc,
  keep ALL qualifying tasks (no per-repo cap). Zero-yield repos are NOT fabricated.
- Overlap with the 3 published cancer editions is allowed (user decision);
  domains are independent selections, not a partition of one repo set.

## Zero-yield repos (informational, 44)

- china-testing/python-api-tesing
- paperclipai/companies
- MinkaiXu/GeoDiff
- vijaymasand/PyChem-Pro
- weisscharlesj/SciCompforChemists
- DeepWism/DeepWism-miRNA
- SMTG-Bham/doped
- MinkaiXu/GeoLDM
- Intelligent-Drug-Discovery-Lab/SurfDock
- MorganCThomas/MolScore
- AnshMittal1811/MachineLearning-AI
- zjunlp/MolGen
- pcko1/Deep-Drug-Coder
- qinheming/BIoClaw
- HFooladi/GNNs-For-Chemists
- Shen-Lab/DeepAffinity
- blazerye/DrugAssist
- mcs07/CIRpy
- THUNLP-MT/dyMEAN
- mims-harvard/PDGrapher
- ml-jku/clamp
- jssweller/DrugHIVE
- benstaf/ChemGAN-challenge
- mooreneural/lacuna
- alvaroprat97/sigmadock
- molML/s4-for-de-novo-drug-design
- Augmented-Nature/ChEMBL-MCP-Server
- qcscine/sparrow
- CataAI/PoseX
- Intelligent-Drug-Discovery-Lab/EquiScore
- Tyche-MKR/scientific-agent-skills
- lmdu/dockey
- CDDLeiden/PCMol
- 1234zou/MOKIT
- ifyoungnet/ADMETlab
- learningmatter-mit/PatentChem
- tencent-quantum-lab/TenCirChem
- Ahey1/Ester-Studio
- SergeiNikolenko/Burette
- rvianello/chemicalite
- UnixJunkie/FASMIFRA
- dylanwal/chemistry_drawer
- RyanZR/labodock
- VicFisher/DiffPhore

## Caveats

- Static validation only; real grading needs an LLM judge key + Docker.
- inline_dockerfile mode skips image build (no Docker daemon needed to publish).
- Provider secrets in upstream diffs were redacted before public release.
