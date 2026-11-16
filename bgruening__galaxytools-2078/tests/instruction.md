# Issue

**Title:** drs-transcript-prediction: auto-generated tool wrapper (issue #2075)

## Description

This PR adds a Galaxy wrapper for **drs-transcript-prediction (TP)**, which predicts transcripts from nanopore direct RNA sequencing reads by locating candidate start/stop sites at read-depth changes within distinct genomic ranges and filtering alternative start/stop combinations via a read-assignment ratio model. The wrapper exposes all 12 CLI options (numeric tuning params grouped in collapsed sections) and produces three outputs: candidate start/stop sites (BED), predicted transcripts (BED), and predicted transcripts (GFF3). Generated files include `drs_transcript_prediction.xml`, `macros.xml` with the version pinned to bioconda 1.0.4, a `.shed.yml`, and real upstream test data (E. coli E2348/69 plasmid DRS reads) with 13 expected output files covering 5 test scenarios; the test data originates from upstream v1.0.5 but was verified to reproduce every expected file byte-for-byte under the packaged 1.0.4. `planemo lint` passes with zero warnings and all 5 tests pass, covering defaults, chromosome restriction with `--candidates_only`, depth and threshold tuning, and stricter ratio filtering, each with file comparisons plus content assertions. No bio.tools entry exists for this tool, so the mBio 2024 paper (via DOI) and the repository are cited instead.

.

---

## Working on this tool

To review or improve this tool locally:

**If you don't have the repo yet** (forks and clones in one step):

```bash
gh repo fork bgruening/galaxytools --clone
cd galaxytools
git checkout tool-bot/issue-2075
```

**If you already have the repo:**

```bash
git fetch origin
git checkout tool-bot/issue-2075
```

The tool files are in `tools/drs-transcript-prediction/`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `345d61c75bf7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.