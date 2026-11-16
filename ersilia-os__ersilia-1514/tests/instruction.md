# Issue

**Title:** Airtable field update and add unit testing

## Description

## Description

#### Overview:
This PR modifies the aitable interface and `BaseInformation` class to incorporate the new fields as below:

```yml
Environment Size # to dependency size
Image Size # model docker image size
Computational Performance 1 # computational performance for 1 input sample
Computational Performance 10 # computational performance for 10 input samples
Computational Performance 100 # computational performance for 100 input samples
```
 Also to add adds unit tests for the `ReadmeMetadata`, `BaseInformation` classes and Mocked Airtable responses are used for tests.

- **`ReadmeMetadata`**: Tests the `write_information()` methods to ensure correct data retrieval and README generation.
- **`BaseInformation`**: Verifies that model attributes (title, description, performance metrics, etc.) are correctly set and retrieved using direct assignment.

#### Tests Added:
- **`test_read_information`**: Confirms correct model data retrieval from Airtable.
- **`test_write_information`**: Ensures the README content is formatted correctly.
- **`test_write_information_to_file`**: Verifies that README content is written to a file.
- **`test_base_information_setter`**: Tests direct assignment of attributes in `BaseInformation`.
- **`test_airtable_interface_ro`**: Verifies Airtable read-only functionality.
- **`test_airtable_interface_rw`**: Verifies Airtable read-write functionality.
- **`test_airtable_metadata_find_record`**: Confirms correct data retrieval from Airtable metadata.

Related to #1484

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5fa3bd8e172d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.