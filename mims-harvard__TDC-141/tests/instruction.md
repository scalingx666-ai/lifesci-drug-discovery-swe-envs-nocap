# Issue

**Title:** New TCR-Epitope Binding Affinity Prediction Task

## Description

. 

The new TCR-Epitope Binding Affinity Prediction Task can be used via: 

`from tdc.multi_pred import TCREpitopeBinding
data = TCREpitopeBinding(name = 'weber',  path = './data')`
 
The 'weber' dataset contains information about TCR full and cdr3 sequence, as well as epitope sequence as amino acids or smiles strings.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0432dea467f3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.