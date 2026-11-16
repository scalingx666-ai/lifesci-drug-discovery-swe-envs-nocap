# Issue

**Title:** New Dataset for Existing Task

## Description

New dataset description: Human/Rat Liver Microsomal Stability (HLM_RLM)

**Describe the problem**
We believe that the HLM_RLM datasets would be beneficially added under the ADME task. The HLM_RLM datasets predict the metabolic stability of compounds in Human and Rat Liver Microsomes, which is crucial for early-stage drug development. The datasets include 6,013 compounds for human liver microsomes and 5,590 for rat liver microsomes. Compounds are classified as stable or unstable based on their half-life. We have sanitized and organized the datasets, derived from a published paper(DOI: 10.1021/acs.chemrestox.2c00207), into a format with three columns: ID, X, and Y.

**Describe the solution you’d like**
from tdc.single_pred import ADME
data = ADME(name = ‘hlm’)
data = ADME(name = ‘rlm’)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d879e2598393`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.