# Issue

**Title:** ci: make routine CI checks manual

## Description

Pushes to main still started routine CI after PR triggers were removed, producing more failure emails. Make Docker, lint and Python verification manual, and remove push triggering from Tests while preserving its release trigger.

Jobs and publishing/deployment workflows are unchanged. Validation: parsed the modified YAML and compared all settings, allowing only removal of push triggers and addition of workflow_dispatch.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b6398ce4d277`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.