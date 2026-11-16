# Issue

**Title:** Refactor/public bucket access

## Description

Refactors the Polaris Hub client and storage modules to simplify authentication handling and allow for public access of artifacts. Key changes include removing authentication for reads, and updating dataset and benchmark retrieval methods to get data path from the API response. 

### Authentication and Session Management Updates:
* Removedauthentication checks for retrieval methods in `PolarisHubClient` and added explicit token validation where necessary, such as in `upload_results` and `upload_model`.
* Introduced a `mode` parameter in `StorageSession` to control authentication requirements, making it optional for read operations but mandatory for write operations. 

### Dataset and Benchmark Handling Improvements:
* Simplified dataset and benchmark retrieval methods by replacing `_base_request_to_hub` with `request` and using metadata fields (`zarr_path`, `table_path`) for loading resources.

### Storage Refactor:
* Replaced custom S3 storage logic for public reads in `StorageSession` with `fsspec` for handling get file and store operations.

### Codebase Simplification:
* Consolidated logic for handling Zarr archives and storage paths across dataset-related methods.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4c3ab4ebb0b7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.