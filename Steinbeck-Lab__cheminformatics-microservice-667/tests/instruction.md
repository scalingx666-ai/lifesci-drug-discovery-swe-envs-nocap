# Issue

**Title:** feat: Hydrogen display to 'smart'

## Description

This pull request introduces support for hand-drawn chemical structure prediction and improves hydrogen display options in molecular depictions. The main changes include adding a `hand_drawn` option throughout the OCSR prediction pipeline, updating the depiction endpoint to allow fine-grained control over hydrogen display, and refactoring the CDK depiction logic for better error handling and highlighting flexibility.

**Hand-drawn chemical structure prediction support:**

* Added a `hand_drawn` boolean parameter to `get_predicted_segments`, `get_predicted_segments_from_file`, and all related API endpoints, allowing users to select the hand-drawn model for SMILES prediction. [[1]](diffhunk://#diff-5909ec1b1ce792350bc51f383f9620c8655cf991b78afc438db749b5c8ef2e13L79-R87) [[2]](diffhunk://#diff-5909ec1b1ce792350bc51f383f9620c8655cf991b78afc438db749b5c8ef2e13L96-R114) [[3]](diffhunk://#diff-5909ec1b1ce792350bc51f383f9620c8655cf991b78afc438db749b5c8ef2e13R123) [[4]](diffhunk://#diff-5909ec1b1ce792350bc51f383f9620c8655cf991b78afc438db749b5c8ef2e13L135-R143) [[5]](diffhunk://#diff-edc206360314e8d296f260bbfa1e8569f044cc7360153f81c1b47b33753ea319R99-R103) [[6]](diffhunk://#diff-edc206360314e8d296f260bbfa1e8569f044cc7360153f81c1b47b33753ea319R113) [[7]](diffhunk://#diff-edc206360314e8d296f260bbfa1e8569f044cc7360153f81c1b47b33753ea319R130) [[8]](diffhunk://#diff-edc206360314e8d296f260bbfa1e8569f044cc7360153f81c1b47b33753ea319R149) [[9]](diffhunk://#diff-edc206360314e8d296f260bbfa1e8569f044cc7360153f81c1b47b33753ea319R176-R184) [[10]](diffhunk://#diff-edc206360314e8d296f260bbfa1e8569f044cc7360153f81c1b47b33753ea319L189-R201)

**Hydrogen display control in molecular depictions:**

* Introduced a `hydrogen_display` parameter to the 2D molecule depiction API, documentation, and the underlying CDK depiction logic, enabling users to choose how hydrogens are rendered (options: Provided, Minimal, Explicit, Stereo, Smart). [[1]](diffhunk://#diff-0a1cedd87d48e1510c67e9d4111c2504bb2102092866774783199123796d28e8R25) [[2]](diffhunk://#diff-0a1cedd87d48e1510c67e9d4111c2504bb2102092866774783199123796d28e8R41-R46) [[3]](diffhunk://#diff-06151d6a4ffb1eb21d05a6c489ae6e881402ff066a07bae03fe11771ff0c91f3R149-R160) [[4]](diffhunk://#diff-06151d6a4ffb1eb21d05a6c489ae6e881402ff066a07bae03fe11771ff0c91f3L161-R202) [[5]](diffhunk://#diff-06151d6a4ffb1eb21d05a6c489ae6e881402ff066a07bae03fe11771ff0c91f3R230-R238)

**Refactoring and improved error handling in CDK depiction:**

* Refactored `get_cdk_depiction` to return a tuple `(encoded_image, mol_imageSVG)` or an error message, added validation for hydrogen display mode, and improved error handling for SMILES parsing and depiction generation. [[1]](diffhunk://#diff-0a1cedd87d48e1510c67e9d4111c2504bb2102092866774783199123796d28e8R41-R46) [[2]](diffhunk://#diff-0a1cedd87d48e1510c67e9d4111c2504bb2102092866774783199123796d28e8R79-R103) [[3]](diffhunk://#diff-0a1cedd87d48e1510c67e9d4111c2504bb2102092866774783199123796d28e8L100-R208)

**Highlighting logic improvements:**

* Moved highlighting logic into a dedicated `_apply_highlighting` helper function, allowing prioritization of explicit atom indices over SMARTS patterns and supporting multiple substructures for highlighting.

**Dependency management:**

* Added missing import for `set_hydrogen_display` from `app.modules.cdk_hydrogen_display` in the depiction module.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e4a4ac00a71`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.