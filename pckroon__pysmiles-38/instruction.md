# Issue

**Title:** init draft aromatic

## Description

This is the initial draft of the new aromaticity algorithm following the ideas outlined [here](https://depth-first.com/articles/2021/06/30/writing-aromatic-smiles/) and [here](https://depth-first.com/articles/2020/02/10/a-comprehensive-treatment-of-aromaticity-in-the-smiles-language/).

The key difference is that we are not trying to assign chemical aromaticity but rather kekulize the molecule (i.e. fixing hcount). In a nutshell, the algorithm proceeds as follows:

1. Assign a preliminary hcount to all non-hydrogen atoms. This is a bit awkward but needed for the next step, because we want to be able to deal with cases where implicit hydrogen are part of the non-aromatic atoms. 
2. Remove all nodes that have a full valance, which we can only assess after implicit hydrogens have been added to non-aromatic residues. 
3. Get the connected components of the resulting fragmented graph. Each component has to be a delocalized system and is potentially aromatic. 
4. For each component we check if there exists a maximum matching and if that matching is perfect. If it is not perfect the delocalized system is written incorrectly and a syntax error is raised. It's like checking if we have perfect alternating single and double bonds. 
5a. If the system is cyclic we assume it to be (anti-)aromatic and give it a bond order of 1.5.  
5b. If it is not cyclic then we simply assign a bond order of 2 to the edges that constitute the perfect matching. 

Some differences in behaviour to the previous version:

| SMILES           | VALID | AROMATIC           | old                     | new   |
|------------------|-------|--------------------|-------------------------|-------|
| c1c[nH]cc1       | yes   | no                 | pass                    | pass  |
| c1cNcc1          | yes   | no                 | pass                    | pass  |
| c1cncc1          | no    | raises Error       | fail (no hydrogen on N) | pass  |
| c1cscc1          | yes   | no                 | fail                    | pass  |
| c1cScc1          | yes   | no                 | pass                    | pass  |
| c1cnc[nH]1       | yes   | no                 | pass                    | pass  |
| c1cncN1          | yes   | no                 | pass                    | pass  |
| N12ccccc1ccc2    | yes   | no                 | pass                    | pass  |
| n12ccccc1ccc2    | yes   | no                 | pass                    | pass  |
| c12ccccc1Ncc2    | yes   | no | pass                    | pass  |
| c12ccccc1[nH]cc2 | yes   | no | pass                    | pass  |
| c12ccccc1ncc2    | no    | raises Error       | fail (no hyrdogen on N) | error |
| c1cscn1          | yes   | no                 | fail                    | pass  |
| cccc             | yes   | no                 | fail (raises Error)     | pass  |
| OCCn2c(=N)n(CCOc1ccc(Cl)cc1Cl)c3ccccc23| yes | partly | fail ( h on aromatic n) | pass |

The molecule from this [blog-post](https://mattermodeling.stackexchange.com/questions/6460/rdkit-and-pysmiles-results-differ-on-some-smiles-strings) mentioned in #19 is also fixed.

Overall I'd say this algorithm is more robust as it raises an Error for hard fails like `c1cncc1` but is also linenet towards chemically intuative smiles like `cccc`. 

The major problems are:

- how to deal with wildcards ? For now they are just ignored because we don't know the valency and bond order. That means `[*]1[*][*]1` is not aromatic anymore.
- how to deal with charges in the intial valance assignment ? I think it should be `missing = valance - bonds + charges`
- how to assing aromarticity for fused rings. Currently napthalene is not aromatic, which might be fine???

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2308e2409368`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.