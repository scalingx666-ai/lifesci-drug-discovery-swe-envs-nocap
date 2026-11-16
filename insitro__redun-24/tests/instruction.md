# Issue

**Title:** AWS Batch executor enhancements: shared memory requirements, and more faithful local dev experience

## Description

Greetings @mattrasmus and team!

This PR adds new capabilities to the AWS Batch Executor.

1. Tasks can specify `shared_memory` as a task option. This will set the "Shared memory size" option in the Batch Job Definition. Some background on this- by default, docker containers are run with a very low 64MB shared memory setting (size of `/dev/shm`). Certain resource-heavy tasks require much more shared memory. In my case, it's training deep neural nets using Pytorch. See [here](https://discuss.pytorch.org/t/training-crashes-due-to-insufficient-shared-memory-shm-nn-dataparallel/26396) for background.

2. When running Batch tasks as local docker containers using `debug=True`, task options for compute resource requirements will now be enforced locally. This applies to `vcpus`, `memory`, `gpus`, and `shared_memory`. This is done using the docker flags `--cpus`, `--memory`, `--gpus` and `--shm`. My original goal here was just to make it possible to run in local containers with high shared memory requirements, but effectively this will make batch debug mode that much more faithful to the behavior in Batch.

If this is a change you'd be interested in merging into redun, great! Happy to update the PR in response to feedback.

Cheers!
Dan Spitz

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `18a16f73930b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.