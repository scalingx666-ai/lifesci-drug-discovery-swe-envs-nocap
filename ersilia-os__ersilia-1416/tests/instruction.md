# Issue

**Title:** Model tester and Inspect command functionality updates

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [x] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [x] Have you written new tests for your core changes, as applicable?
- [x] Have you successfully ran tests with your changes locally?

**Description**

This PR introduces a significant refactor of the `ModelTester`  and  `Inspect` class to enhance its functionality and usability. The updates include:  

### Key Enhancements:  
1. **Support for `ersilia-pack` Models:**  
   - The class now supports models packaged with `ersilia-pack`.  

2. **Remote Repository Integration:**  
   - Added support for testing models from remote repositories using the `--remote` flag.  

3. **Integration with `--inspect` Command:**  

 - **High-Level Checks:**  
   - Model metadata validation.  
   - Model size calculation.  
   - Folder structure checks.  
   - File integrity checks.  
   - And more.  

4. **Detailed Inspection with `--level/-l deep` Flag:**  
   - A deeper inspection can now be performed to include:  
     - Testing with a single input.  
     - **Model consistency output:** Comparing outputs from running `run.sh` and the Ersilia `run` command.  
     - Computational performance assessment.  
     - Repository structure validation, detection of extra/unnecessary files, and more.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9e0780422f0a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.