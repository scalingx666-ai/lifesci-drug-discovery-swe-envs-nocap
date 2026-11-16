# Issue

**Title:** docs: clarify atom featurizer CLI help

## Description

## Description

Improves the CLI help text for `--multi-hot-atom-featurizer-mode` by clarifying that the option selects the atom feature encoding scheme used during featurization.

## Example / Current workflow

The previous help text described the available featurization modes but did not clearly state that the argument controls the atom feature encoding scheme itself.

## Bugfix / Desired workflow

The updated help text makes the purpose of the argument more explicit while preserving all existing functionality and documentation.

## Changes

* Clarified the help text for `--multi-hot-atom-featurizer-mode`
* No functional changes
* No API changes
* No model behavior changes

## Testing

Documentation-only change. No tests required.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `34656ef22e80`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.