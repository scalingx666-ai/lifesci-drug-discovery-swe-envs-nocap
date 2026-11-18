# Issue

**Title:** Reorganize ONNX into subpackage and fix ONNX/PyTorch drift

## Description

- Moved all ONNX code from flat files into a dedicated mlconfgen/onnx/ subpackage (conformer_generator.py, equivariant_diffusion.py, molgraph.py, utils.py)                                               
- Extracted shared constants and pure-RDKit functions into utils/common.py to eliminate duplication between PyTorch and ONNX paths                                                                        
- Fixed ONNX:                                                                                                                                                                                      
- sample_center_gravity_zero_gaussian_with_mask: np.random.rand (uniform) → np.random.randn (Gaussian) to match PyTorch                                                                                 
- prepare_edm_input_onnx: added pad_to parameter to match PyTorch signature

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d2e6171784bf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.