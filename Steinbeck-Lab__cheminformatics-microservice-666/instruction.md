# Issue

**Title:** feat: Hydrogen display to 'smart'

## Description

This pull request introduces support for hand-drawn chemical structure prediction and improves hydrogen display options in molecular depictions. The most significant changes are the addition of a `hand_drawn` parameter to relevant prediction endpoints and functions, and the enhancement of the depiction API to allow fine-grained control over hydrogen atom visualization. These updates improve flexibility for users working with hand-drawn images and provide more accurate and customizable molecular representations.

**Hand-drawn image prediction support:**

* Added a `hand_drawn` boolean parameter to `get_predicted_segments`, `get_predicted_segments_from_file`, and all relevant OCSR API endpoints and handlers, enabling the use of a specialized model for hand-drawn chemical structure images. [[1]](diffhunk://#diff-5909ec1b1ce792350bc51f383f9620c8655cf991b78afc438db749b5c8ef2e13L79-R87) [[2]](diffhunk://#diff-5909ec1b1ce792350bc51f383f9620c8655cf991b78afc438db749b5c8ef2e13L96-R114) [[3]](diffhunk://#diff-5909ec1b1ce792350bc51f383f9620c8655cf991b78afc438db749b5c8ef2e13R123) [[4]](diffhunk://#diff-5909ec1b1ce792350bc51f383f9620c8655cf991b78afc438db749b5c8ef2e13L135-R143) [[5]](diffhunk://#diff-edc206360314e8d296f260bbfa1e8569f044cc7360153f81c1b47b33753ea319R99-R103) [[6]](diffhunk://#diff-edc206360314e8d296f260bbfa1e8569f044cc7360153f81c1b47b33753ea319R113) [[7]](diffhunk://#diff-edc206360314e8d296f260bbfa1e8569f044cc7360153f81c1b47b33753ea319R130) [[8]](diffhunk://#diff-edc206360314e8d296f260bbfa1e8569f044cc7360153f81c1b47b33753ea319R149) [[9]](diffhunk://#diff-edc206360314e8d296f260bbfa1e8569f044cc7360153f81c1b47b33753ea319R176-R184) [[10]](diffhunk://#diff-edc206360314e8d296f260bbfa1e8569f044cc7360153f81c1b47b33753ea319L189-R201)

**Hydrogen display options for molecular depictions:**

* Introduced a `hydrogen_display` parameter to the depiction API (`depict_2d_molecule`), allowing users to select modes such as "Provided", "Minimal", "Explicit", "Stereo", or "Smart" for hydrogen atom visualization. Updated documentation and function signatures to reflect this feature. [[1]](diffhunk://#diff-06151d6a4ffb1eb21d05a6c489ae6e881402ff066a07bae03fe11771ff0c91f3R149-R160) [[2]](diffhunk://#diff-06151d6a4ffb1eb21d05a6c489ae6e881402ff066a07bae03fe11771ff0c91f3L161-R202) [[3]](diffhunk://#diff-06151d6a4ffb1eb21d05a6c489ae6e881402ff066a07bae03fe11771ff0c91f3R230-R238) [[4]](diffhunk://#diff-0a1cedd87d48e1510c67e9d4111c2504bb2102092866774783199123796d28e8R25) [[5]](diffhunk://#diff-0a1cedd87d48e1510c67e9d4111c2504bb2102092866774783199123796d28e8R41-R46)
* Refactored the depiction logic in `get_cdk_depiction` to apply the selected hydrogen display mode using the new `set_hydrogen_display` helper, and improved error handling for invalid modes. [[1]](diffhunk://#diff-0a1cedd87d48e1510c67e9d4111c2504bb2102092866774783199123796d28e8R9) [[2]](diffhunk://#diff-0a1cedd87d48e1510c67e9d4111c2504bb2102092866774783199123796d28e8L51-R58) [[3]](diffhunk://#diff-0a1cedd87d48e1510c67e9d4111c2504bb2102092866774783199123796d28e8R79-R103)

**Depiction and highlighting improvements:**

* Modularized the highlighting logic in molecular depictions by introducing the `_apply_highlighting` helper, which prioritizes explicit atom indices over SMARTS pattern matching and improves error handling for invalid patterns.

These changes enhance both the accuracy and usability of chemical structure recognition and visualization in the application.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `897f73870a02`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.