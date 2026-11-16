# Issue

**Title:** Fix model with graph transform mutates input batch molgraph

## Description

While working on  I found that passing a BatchMolGraph through a chemprop model twice gave different results. This is because the GraphTransform mutates the input. This isn't a big issue because I expect people usually just get the BatchMolGraph fresh from the dataloader. But I also think it is unexpected that the model mutates the input. In that PR, my `InteractionMPNN` class needs to reorder the nodes in the graph, but I didn't want it to mutate the input. I found that doing a shallow copy worked well because the underlying tensors are not duplicated (saves time and memory) and assigning a new tensor to one of the attributes (like V) doesn't make Python lose reference to the original input tensor. 

One question: I included a comment about this. Normally we try to limit the comments in the chemprop codebase. A user could look at the git blame to find this PR which describes why we use `copy.copy`. But in this case, I am slightly inclined to include a comment because someone might think copying the bmg is unusual. Open to thoughts on this though.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `568db39041a2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.