# Issue

**Title:** fix(be): count the subjects behind each FDA row's ratio in n

## Description

For the FDA frameworks the n column counted every subject with the test or the reference formulation, although the reference-scaled criterion uses the intra-subject contrasts, which keep only the subjects with every administration their sequence calls for.  With one subject missing a reference administration, an RSABE row decided by the scaled bound reported n = 24 for a ratio estimated from 23 subjects.

n now counts the subjects behind the ratio the row shows (the estimate the decision used): the intra-subject contrast subjects when the reference-scaled criterion decides, and every subject with either formulation when the model decides (the RSABE fallback, NTID, HVNTID). The caption states this, be_extract_param() reports the contrast count as isc_n, and the expanding-limits frameworks are unchanged.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a6b5f0563813`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.