# Issue

**Title:** Fix overly broad donor SMARTS in the pharmacophore tutorial

## Description

## Problem

Following the request to check other feature definitions after #9783, the pharmacophore tutorial's `MinimalFeatures.fdef` has an overly broad donor expression:

`[{NDonor},{ChalcDonor},!$([D1]-[C;D3]=[O,S,N])]`

The final comma makes the carbonyl-adjacent exclusion a third **OR** alternative. Any atom not matching that exclusion becomes a donor. Reading the shipped tutorial factory on methane (`C`) returns a donor at atom 0; ethane returns two, and dimethyl ether labels all three atoms as donors.

## Change

Use the low-precedence AND (`;`) so the rule means `(NDonor OR ChalcDonor) AND NOT exclusion`. This applies the existing minimal factory's exclusion to both alternatives; it does not change the production `Data/BaseFeatures.fdef` or redefine the full feature set.

Add exact donor-atom regressions for methane, ethane, dimethyl ether, methanol, methylamine, methanethiol, ammonium, pyrrole and the retained acetic-acid exclusion. Regenerate the dependent fingerprint examples in both English and Japanese documentation.

## Verification

- Actual feature-factory reproduction before the fix: methane, ethane and ether carbons incorrectly appear as donors. After the fix those non-donors produce no donor features; positive nitrogen/oxygen/sulfur/charged/aromatic cases match the expected atom IDs.
- `testChemicalFeatures.py`: **11 passed**, including the new regression's nine molecular subcases. The new test failed before the definition change.
- Targeted tutorial examples executed with Python `doctest`: **27/27 English**, **27/27 Japanese**.
- Actual Pharm2D fingerprint generation for the documented molecule: 13 set bits instead of the incorrect 57; 9 with PosIonizable disabled. Both docs now match the generated fingerprints.
- Separate read-only AI review found no blocker; its Japanese-doc observation was addressed.

Runtime used installed RDKit **2026.09.1**, with the changed source-tree feature definition loaded by `ChemicalFeatures.BuildFeatureFactory`. No new C++ build, full RDKit suite, model-quality improvement or production-wide donor change is claimed.

Follow-up to

## Review and assistance

I supervised and checked the AI-assisted work as it progressed. AI assistance used OpenAI Codex through omp for investigation, implementation and verification. No maintainer review or approval is claimed. Verification was CPU-only; no GPU validation is claimed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2bbaa851cb56`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.