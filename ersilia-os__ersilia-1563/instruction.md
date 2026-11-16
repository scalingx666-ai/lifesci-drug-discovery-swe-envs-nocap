# Issue

**Title:** Packing with Ersilia Pack now resolved columns from columns file name, avoiding issues with schema resolution

## Description

Thank you for taking your time to contribute to Ersilia, just a few checks before we proceed
- [x] Have you followed the guidelines in our [Contribution Guide](https://github.com/ersilia-os/ersilia/blob/master/CONTRIBUTING.md)
- [ ] Have you written new tests for your core changes, as applicable?
- [x] Have you successfully ran tests with your changes locally?

**Description**

Packing with Ersilia Pack now resolved columns from columns file name, avoiding issues with schema resolution

Below is a Copilot-generated summary: 
This pull request includes several changes to enhance the functionality and error handling of the FastAPI model sniffing process in the Ersilia project. Key changes involve adding new exception classes, updating the `BuiltinExampleReader` class, and introducing a new `ColumnsFileReader` class.

Enhancements to FastAPI model sniffing:

* [`ersilia/hub/fetch/actions/sniff_fastapi.py`](diffhunk://#diff-f30ea9b47db6164748dc5b7c570c7db927622d4d43f59d92408759f81973b4c7L7-L16): Added new utility classes and methods to handle input and output examples, column names, and types. This includes renaming methods in `BuiltinExampleReader` and adding a new `ColumnsFileReader` class to manage column-related data. [[1]](diffhunk://#diff-f30ea9b47db6164748dc5b7c570c7db927622d4d43f59d92408759f81973b4c7L7-L16) [[2]](diffhunk://#diff-f30ea9b47db6164748dc5b7c570c7db927622d4d43f59d92408759f81973b4c7L30-R70) [[3]](diffhunk://#diff-f30ea9b47db6164748dc5b7c570c7db927622d4d43f59d92408759f81973b4c7R79-R89) [[4]](diffhunk://#diff-f30ea9b47db6164748dc5b7c570c7db927622d4d43f59d92408759f81973b4c7R98-R198) [[5]](diffhunk://#diff-f30ea9b47db6164748dc5b7c570c7db927622d4d43f59d92408759f81973b4c7R238-R274)

Error handling improvements:

* [`ersilia/utils/exceptions_utils/fetch_exceptions.py`](diffhunk://#diff-f30ea9b47db6164748dc5b7c570c7db927622d4d43f59d92408759f81973b4c7L7-L16): Introduced new exception classes `SniffFastApiColumnsDontMatch` and `SniffFastApiColumnTypesIncompatibility` to handle specific errors related to column mismatches and type incompatibilities during the schema sniffing process. [[1]](diffhunk://#diff-f30ea9b47db6164748dc5b7c570c7db927622d4d43f59d92408759f81973b4c7L7-L16) [[2]](diffhunk://#diff-e6e1dadab6e6551629767abdcb5258c2728215d3a2ae74c0905c207bf76a593cR192-R223)

Logging updates:

* [`ersilia/hub/delete/delete.py`](diffhunk://#diff-9c2fa7ae8d0510a1c43bdfc77c49f448f3e645cdd38240a8fdefa47285585d3dR278-R280): Added debug logging to the `_delete` method to track the process of looking for and finding the BentoML catalog.

These changes collectively improve the robustness and clarity of the FastAPI model sniffing process, ensuring better error handling and more informative logging.

**Changes to be made**

No changes expected in the near future.

**Status**

I have tested it for model eos3b5e and it works.

**To do**

- [ ] At the moment, this only works on "run" api endpoints. We may want to extend it in the future.
- [ ] We have added a lot of logging that may affect the BentoML deployment. This needs to be cleaned.

Is this pull request related to any open issue? If yes, replace issueID below with the issue ID

Related to #1562

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `07955c9605dc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.