# Issue

**Title:** Remove unnecessary methods and attributes

## Description

molpipeline/abstract_pipeline_elements/core.py
- [x] remove method `copy` from `ABCPipelineElement`
- [x] remove finish method from ABCPipelineElement
- [x] remove method `additional_attributes` from `ABCPipelineElement`
- [x] remove method `to_json`  from `TransformingPipelineElement`

molpipeline/any2mol/sdf2mol.py
- [x] remove enumeration of SDFToMol
- [x] remove `finish` method from SDFToMol
molpipeline/pipeline/_molpipeline.py
- [x] remove `finish` method from _Molpipeline

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `75e6dea45864`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.