# Issue

**Title:** Improve stereoisomer detection

## Description

This PR addresses the issue #55. By accessing the number of stereocenters in the molecules, most of the enantiomers or diastereomers can be detected. This PR added detection of E/Z diastereomers which are double bond isomers. Thus, most of the cases of stereoisomers can be covered in the curation module. 

## Changelogs
- Added detection of E/Z diastereome
- Fixed a typo for `polaris.curation.viz_utils.visualize_distribution`

---

For the exceptional scenario, such as meso isomers, can only be inspected visually. 

This PR depends on changes in

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `20cea5d6ff9b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.