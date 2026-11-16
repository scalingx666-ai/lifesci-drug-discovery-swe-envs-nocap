# Issue

**Title:** Fix citation format in cellpose.xml

## Description

The citation was not shown on Galaxy:

<img width="1271" height="1030" alt="Bildschirmfoto 2026-08-03 um 17 49 01" src="https://github.com/user-attachments/assets/2c1ff17a-c5f6-4b74-830b-aaed9de371e7" />

This is probably due to the spurious URL prefix of the DOI.

This PR removes that prefix.

The tool version is not incremented, so the fix will be deferred until the tool receives some more substantial updats.

---

FOR CONTRIBUTOR:
* [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
* [x] License permits unrestricted use (educational + commercial)
* [ ] This PR adds a new tool or tool collection
* [x] This PR updates an existing tool or tool collection
* [ ] This PR does something else (explain below)

There are two labels that allow to ignore specific (false positive) tool linter errors:

* `skip-version-check`: Use it if only a subset of the tools has been updated in a suite.
* `skip-url-check`: Use it if github CI sees 403 errors, but the URLs work.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `06becad57576`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.