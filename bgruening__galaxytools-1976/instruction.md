# Issue

**Title:** datavzrd: auto-generated tool wrapper (issue #1966)

## Description

This PR adds a Galaxy wrapper for **datavzrd** (v2.71.3, ), a tool for rendering interactive, configurable HTML reports from tabular data.

The wrapper supports multiple tabular inputs (CSV/TSV/JSON/Parquet), with either auto-generated configs (`datavzrd suggest`) or user-provided YAML configs whose dataset paths are rewritten via the included `datavzrd_config.py` helper. Reports are exposed as interactive Galaxy HTML output (QUAST-style directory layout) or as a zip archive, with advanced options for max-in-memory-rows, webview controls, and output overwriting.

The PR includes `datavzrd_render.xml`, shared `macros.xml`, the config helper script, `.shed.yml` metadata, and test data adapted from upstream examples. All 5 functional tests pass under planemo, covering auto-config, multi-input, user config, TSV, and zip output scenarios.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b74c5f82d734`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.