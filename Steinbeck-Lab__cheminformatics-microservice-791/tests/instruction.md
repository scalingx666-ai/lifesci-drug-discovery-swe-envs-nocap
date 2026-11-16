# Issue

**Title:** feat: structure input auto-detect

## Description

## Summary
- Add centralized structure format detection and parsing in the toolkit layer (InChI, SELFIES, molblock, XYZ, SMILES, IUPAC) with SMILES-only behavior preserved by default.
- Expose opt-in auto-detect via `GET /convert/detect-format`, optional `input_format` on batch conversion, and `auto_detect=true` on single-molecule convert/chem/depict/tools endpoints.
- Integrate backend format detection in the format conversion UI with a local regex fallback and `auto_detect` on downstream convert calls.

## Test plan
- [ ] `pytest tests/test_format_detection.py tests/test_helper.py tests/test_converters.py`
- [ ] `GET /latest/convert/detect-format?input=InChI=1S/C2H6O/c1-2-3/h3H,2H2,1H3` returns `inchi` with high confidence
- [ ] Existing SMILES-only calls without `auto_detect` behave unchanged
- [ ] `POST /latest/convert/batch` with omitted `input_format` auto-detects InChI/SELFIES
- [ ] Format conversion UI auto-detects pasted input and converts with `auto_detect=true`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b7da78fc71bc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.