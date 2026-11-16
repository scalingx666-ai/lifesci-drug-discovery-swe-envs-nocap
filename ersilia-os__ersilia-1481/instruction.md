# Issue

**Title:** Support versioning of Dockerized models

## Description

Add functionality to specify image tags and use the latest default tag otherwise.

Through this PR, now we can fetch dockerized ersilia models as follows:

```
ersilia fetch eos3b5e --version 2024-12-26  # Depending on ersilia to figure out fetching from DockerHub

ersilia fetch eos3b5e --from_dockerhub --version 2024-12-26 # Explicitly specifying the fetching mode
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c41fb346609b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.