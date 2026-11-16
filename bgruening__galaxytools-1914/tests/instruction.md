# Issue

**Title:** motus DB fetcher: make temp cleanup resilient to Lustre rmtree race

## Description

download_untar_store() copies the fetched DB out and then removes its scratch dir with shutil.rmtree(). On parallel/network filesystems (e.g. Lustre/corral4) readdir can return stale entries mid-walk, so rmtree raises OSError [Errno 39] "Directory not empty" even though the DB was stored successfully - failing the whole job on a non-essential cleanup. Retry the removal a few times, then ignore errors as a last resort.

Bumps the tool version to 3.1.0+galaxy1.

FOR CONTRIBUTOR:
* [ ] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [ ] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [ ] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

There are two labels that allow to ignore specific (false positive) tool linter errors:

* `skip-version-check`: Use it if only a subset of the tools has been updated in a suite.
* `skip-url-check`: Use it if github CI sees 403 errors, but the URLs work.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ddc991f97e2d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.