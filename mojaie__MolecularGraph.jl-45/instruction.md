# Issue

**Title:** Add substructure 1:1 node matching

## Description

When you want to preserve some property indexed to the nodes,
it's helpful to construct the node map.

I wasn't sure if this functionality already existed by other means. For my application, the `nodeset` approach in  is not sufficient because I want to be able to map the specific atoms between the structures. Specifically, I want to do 3d alignment to a steroid backbone, and so I want to know how to map the [standard steroid carbon numbering system](https://en.wikipedia.org/wiki/Steroid#/media/File:Trimethyl_steroid-nomenclature.svg) between two structures.

~This currently fails because it seems there's some overly-permissive SMARTS matching, so even if this functionality exists and I just missed it, at least the test should be useful.~ Nevermind, I missed the need to supply `nodematcher`!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `88444326cfb0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.