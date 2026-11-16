# Issue

**Title:** MMCIF reader optimization

## Description

Hi,
I found that the same molecule may be way longer to open in mmcif than in mmtf format.
(1.5s for the mmtf, 33s for the mmcif. download link at end of post).

I discovered that in the mmcif reader, the residues were stored in a map before been added in the topology. But this intermediate structure change the order of the residues comparing to the order in the file (sort by chain ID).
And then, when we iterate over the residues to add the standard bonds, and because the residues don't have their initial sort, some bonds with atom of far IDs may be added early in the topology which will implies a lot of insertions. And because the bonds are stored in a "sorted_set", which in reality hide a vector, all these insertions may have a really big cost.

By adding an indirection, we can keep the residue order declared in the file and reduce drasticaly the number of insertions.

After this modification, the same molecule is opened at the same speed in mmtf or mmcif format.

Example file download links :
mmcif : https://www.rcsb.org/structure/7CGO
mmtf : https://mmtf.rcsb.org/v1.0/full/7cgo

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b2ad6c60d0bf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.