# Issue

**Title:** Fragmenter for circular substructures analogous to HOSE code / Morgan fingerprints / molecular signatures

## Description

Even though several places where this methodology is used are already there in CDK, I could not find a way to extract circular substructures as atom containers. Hence, I implemented this fragmenter. What do you think, is this worth integrating?

I had to adjust the dependencies of the cdk-fragment module a bit. I hope this is okay.

The functionality is extensively tested in the accompanying test class, and I ran it over the entire COCONUT natural products database without any issues.

And yes, the AIs helped me a bit here, but I reviewed everything myself.

Let me know what you think.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d460802f116a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.