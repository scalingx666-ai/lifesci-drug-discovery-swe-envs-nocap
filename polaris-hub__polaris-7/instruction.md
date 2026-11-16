# Issue

**Title:** First version of automated dataset curation module

## Description

## Changelogs

- First version of automated data curation module [MolecularCurator](https://github.com/datamol-io/polaris/blob/195d585fd77f328d36c5b91d36ab3ca190c73738/polaris/curation/_curator.py#L9C7-L9C15). It's consisted of [chemistry curation](https://github.com/datamol-io/polaris/blob/195d585fd77f328d36c5b91d36ab3ca190c73738/polaris/curation/_chemistry_curator.py#L65C5-L65C27) and [data curation](https://github.com/datamol-io/polaris/blob/195d585fd77f328d36c5b91d36ab3ca190c73738/polaris/curation/_data_curator.py#L131C5-L131C22). 
Data curator allows to detect stereoisomer activity cliff and class conversion if data thresholds are provided.
- Added  5 types of automatic [outlier detection methods](https://github.com/datamol-io/polaris/blob/741b0250a7bbfa2edf05965724c8529f3f1b1c2f/polaris/curation/utils.py#L211C9-L211C9). Warnings will be raised if outliers exist in the dataset. 
---

_Checklist:_

- [x] _Add tests to cover the fixed bug(s) or the new introduced feature(s) (if appropriate)._
- [x] _Update the API documentation is a new function is added, or an existing one is deleted._
- [x] _Write concise and explanatory changelogs above._
- [x] _If possible, assign one of the following labels to the PR: `feature`, `fix` or `test` (or ask a maintainer to do it for you)._
- [ ] Refactor class and validator with pydantic 
---

_discussion related to that PR_

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0092b80e3950`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.