# Issue

**Title:** Adding MSA server security

## Description

## Summary

This PR adds security/authentication support for calling custom MSA servers in Boltz, enabling the use of both basic authentication and API token authentication when accessing protected MSA endpoints.

## Changes

- **MSA Server Authentication Support:**
  - Added support for **Basic Authentication** using `--msa_server_username` and `--msa_server_password` CLI options, or via the `BOLTZ_MSA_USERNAME` and `BOLTZ_MSA_PASSWORD` environment variables.
  - Added support for **API Key/Token Authentication** using `--api_key_header` and `--api_key_value` CLI options, or via the `MSA_API_KEY_VALUE` environment variable.
  - Ensured only one authentication method (basic or API key) can be used at a time, with clear error messages if both are provided.
  - Authentication is now properly passed to all MSA server requests.

- **Documentation:**
  - Updated the README to clearly explain both authentication methods, including usage examples and environment variable support.
  - Clarified that only one authentication method can be used at a time.

## Motivation

Many custom MSA servers require authentication for access. This PR enables Boltz users to securely provide credentials—either via basic auth or API token—when calling such servers, making Boltz compatible with a wider range of enterprise and protected deployments. Additionally if no authentication is required, everything works as before so it is simply optional.

See the "Authentication to MSA Server" section in the README for details and usage examples.
These changes make it easier for users to securely provide credentials for MSA server access, reduce confusion around environment variable names, and ensure the documentation matches the actual code behavior.

See the "Authentication to MSA Server" section in the README for details and usage examples.
s

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6fa9f4c19084`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.