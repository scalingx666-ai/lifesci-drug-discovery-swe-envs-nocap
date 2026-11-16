# Issue

**Title:** WhisperX: read NLTK punkt_tab from a private copy (fixes alignment on usegalaxy.eu)

## Description

WhisperX 3.8.6+galaxy0 fails on usegalaxy.eu at the alignment step:

```
RuntimeWarning: NLTK will not read data from '/data/db/models/whisperx/whisperx_models/nltk_data': it is writable by, or owned by, another account ...
LookupError: Resource 'punkt_tab' not found.
```

NLTK 3.10 (in the container) only reads data folders that are owned by the job user or root and that no one else can write to. A shared model folder downloaded by an admin is usually owned by another account, so every job that aligns fails. NLTK has no setting to turn this check off.

**Fix:** before running WhisperX, the tool copies `nltk_data/tokenizers/punkt_tab` (11 MB) into a private folder in the job directory (`mktemp -d`, then `chmod -R go-w`, since jobs may run with umask 002) and points `NLTK_DATA` there. This works whoever owns the shared files, so admins don't need to change permissions. If the folder has no `punkt_tab`, nothing is copied and the run behaves as before. That also keeps the CI tests, which run without models, unchanged.

**Tested** offline (`--network none`) in `quay.io/galaxy/whisperx:3.8.6`, with a group-writable `nltk_data` to reproduce the EU failure, and with a job umask of 002:
- old command: `LookupError: Resource 'punkt_tab' not found`, as on EU;
- new command: works, `[SPEAKER_00]: 21 year old Jesus joined Manchester City ...` (tiny model, alignment and diarization).

Version: 3.8.6+galaxy1.

FOR CONTRIBUTOR:
* [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [x] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [x] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `306571e34234`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.