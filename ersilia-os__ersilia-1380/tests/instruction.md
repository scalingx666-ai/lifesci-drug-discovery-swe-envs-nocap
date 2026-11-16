# Issue

**Title:** Make ersilia metadata file agnostic

## Description

This PR does a couple of things, but the main goal is build compatibility with Ersilia Pack's metadata storage format.

1. Reading metadata within ersilia is now agnostic of which format the metadata file follows, ie whether it is a JSON file or a YAML file (following the new template)
2. I've implemented a custom loader class for parsing the YAML file so it always loads the metadata in the data structure that is expected throughout ersilia. 
3. Parts of the code that tried to read metadata from the metadata file now use a util function, `get_metadata_from_base_dir`, found in `utils/paths` to get the metadata. This method looks for either the JSON or the YAML file and if neither is found, raises a `FileNotFoundError`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `14c8828c3562`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.