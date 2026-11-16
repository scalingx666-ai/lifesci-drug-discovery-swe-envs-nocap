# Issue

**Title:** add kMetaShot Reference 2026-09-10

## Description

FOR CONTRIBUTOR:
* [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [ ] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [x] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

There are two labels that allow to ignore specific (false positive) tool linter errors:

* `skip-version-check`: Use it if only a subset of the tools has been updated in a suite.
* `skip-url-check`: Use it if github CI sees 403 errors, but the URLs work.

I served DM after linting and testing to check the ability to correctly download the reference and it works with following command:

`planemo serve /Users/giuseppedefazio/Documents/RTDA_UniBA/periodo_friburgo/lavoro/kMetaShot/galaxy_wrapping/kMS_wrapper/galaxytools/data_managers/data_manager_kmetashot/data_manager/kmetashot_datamanager.xml /Users/giuseppedefazio/Documents/RTDA_UniBA/periodo_friburgo/lavoro/kMetaShot/galaxy_wrapping/kMS_wrapper/galaxytools/tools/kmetashot/kmetashot.xml  --galaxy_root /Users/giuseppedefazio/Documents/RTDA_UniBA/periodo_friburgo/lavoro/kMetaShot/galaxy_wrapping/kMS_wrapper/galaxy
`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `86f48bc65a5c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.