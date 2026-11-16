# Issue

**Title:** SEM image analysis: DiameterJ with Auto thresholding

## Description

This PR adds a SEM image analysis tool based on Fiji, [DiameterJ](https://imagej.net/plugins/diameterj) with different [Auto-thresholding](https://imagej.net/plugins/auto-threshold) methods

It supports three segmentation methods:

- All auto-thresholding methods (17)
- Recursive Statistical Region Merging (SRM) (https://imagej.net/plugins/statistical-region-merging) followed by all auto-thresholding methods 
- Mixed (SRM + All auto-thresholding methods) - non recursive

Discussion:
https://gitlab.cc-asp.fraunhofer.de/materialvital-digital/orga/-/work_items/97

@bgruening @paulzierep: we can share this tool with our collaborators and ask their feedback

Analysis image:

[PVA-A_004.tif](https://github.com/user-attachments/files/31553804/PVA-A_004.tif)
<img width="1024" height="943" alt="PVA-A_004" src="https://github.com/user-attachments/assets/31ee7426-9c90-4c82-b974-808e202bc0d9" />

Analysed by collaborators

- With Huang auto-thresholding

<img width="2053" height="1691" alt="PVA-A_004_T1_Compare" src="https://github.com/user-attachments/assets/61486f2f-57bc-4d94-88a4-62de946283d5" />

- Huang auto-thresholding with Galaxy tool (this PR)

<img width="2053" height="1773" alt="input__auto_thresholding_huang_Compare_Galaxytool_T1" src="https://github.com/user-attachments/assets/16c7dc1a-b880-46b4-916c-2c17ade78536" />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b74c5f82d734`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.