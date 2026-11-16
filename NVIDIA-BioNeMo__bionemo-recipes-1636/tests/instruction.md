# Issue

**Title:** evo2 SAE eval: label producers + probing harness (on #1629)

## Description

## Summary
Evo2 SAE **eval: label producers + probing harness** — turn DNA into an `ActivationBuffer` (the one model-touching step) and score it through the probing CLI (AUROC / annotate / linear / domain-F1 / loss-recovered). Lives in the **`evo2_sae.eval.probing`** package, alongside the #1629 primitives.

**Stacked on #1629** (→ #1622). #1630 supplies the eval labels.

## Contents — `evo2_sae.eval.probing`
- `evo2_buffer.py` — DNA → `ActivationBuffer` (the only model-touching code: Evo2 → layer-L residual → `SAE.encode` + per-token labels)
- `labelers.py` — per-token biological labelers (genetic code / CDS frame; prokaryotic gene calling via `pyrodigal`)
- `annot_tracks.py` — BED/GFF interval-track loader → per-token masks (RefSeq / Rfam / JASPAR / ENCODE)
- `euk_windows.py` — eukaryotic gene-structure windows
- `probe.py` — the probing CLI (`extract` / `auroc` / `annotate` / `linear` / `euk-f1` / `domain-eval`)
- `probe_loss_recovered.py` — SAE fidelity (loss recovered); reuses the shared `sae.eval.loss_recovered`

Imports are package-relative; the primitives come from `evo2_sae.eval.probing`. `loss_recovered` stays in the shared `sae` lib (used by esm2/codonfm too).

## How to run
```bash
cd interpretability/sparse_autoencoders/recipes/evo2
bash .ci_build.sh && source .ci_test_env.sh        # or: PYTHONPATH=src:../../sae/src
pytest tests/test_probe_integration.py tests/test_labelers.py tests/test_annot_tracks.py tests/test_euk_windows.py
# CLI: python -m evo2_sae.eval.probing.probe extract|auroc|annotate|linear|domain-eval ...
```
No dedicated CI lane (deferred — ; CI should fold into the repo-wide recipe lane later).

## Tests
- **CPU (no model):** label producers (`labelers` / `annot_tracks` / `euk_windows`) + the probe-CLI integration (buffer save/load roundtrip incl. the dense twin, AUROC/annotate/linear over a planted feature, `domain_f1` over interval tracks). **35 passed.**
- **GPU:** the real-engine buffer/loss-recovered path is gated by `@pytest.mark.skipif(not torch.cuda.is_available())` — runs on a GPU box, skips otherwise.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `73c261fcbaa6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.