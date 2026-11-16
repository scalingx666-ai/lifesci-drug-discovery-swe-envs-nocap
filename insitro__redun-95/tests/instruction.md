# Issue

**Title:** Specify vcpu and memory as resourceRequirements in AWS Batch executor

## Description

When trying to use redun with AWS Batch on Fargate using the existing `AWSBatchExecutor`, we get the following error:
```
botocore.errorfactory.ClientException: An error occurred (ClientException) when calling the SubmitJob operation: vcpus is not applicable for Fargate. Use resource requirements instead.
```
As it turns out, it looks like specifying `vcpu` and `memory` directly on `containerProperties` is now deprecated (see [here for vcpu](https://docs.aws.amazon.com/batch/latest/APIReference/API_ContainerProperties.html#Batch-Type-ContainerProperties-vcpus) and [here for memory](https://docs.aws.amazon.com/batch/latest/APIReference/API_ContainerProperties.html#Batch-Type-ContainerProperties-memory)) in favor of specifying them in the [`resourceRequirements`](https://docs.aws.amazon.com/batch/latest/APIReference/API_ContainerProperties.html#Batch-Type-ContainerProperties-resourceRequirements) array, so that's the update provided here.

This update will allow running on Fargate with the AWSBatchExecutor.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8c61f27b1f43`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.