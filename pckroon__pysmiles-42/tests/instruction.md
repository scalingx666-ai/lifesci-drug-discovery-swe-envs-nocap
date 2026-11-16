# Issue

**Title:** Use charges for determining valence

## Description

Here I figure out the valence of atoms by assigning electrons to orbital shells, and figuring out with how many unpaired electrons we have left.
Currently, I assume all paired electrons can be excited to higher shells, which deals with multivalent elements (S, P, ...). This does mean that N can also make 5 bonds if you ask it nicely. The *real* solution would be to figure out the balance between the excitation energy on one hand, and the electron unpairing + bond energy on the other, but that sounds really hard. So either we accept this slightly strange behaviour, or we limit this excitation to higher shells only. Further consideration: should the excitation be limited to just 2 electrons, to the next s-orbital?

Still a draft, since I need to iron out some failing tests.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a1684afb91e4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.