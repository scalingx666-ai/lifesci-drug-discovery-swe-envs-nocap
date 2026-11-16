# Issue

**Title:** Security: pin minimum dependencies

## Description

Updates packages to recommended minimum versions per [python](https://discuss.python.org/t/information-for-python-users-regarding-emudhra-emsign-ca-certificate-security-incident/109576) and [conda](https://conda.org/blog/2026-10-21-emudhra-security-updates/) core development teams after [recent CA cert compromise](https://emudhra.we-have-a-problem.com/)

| package | recommended minimum version |
| -- | -- |
| certifi | [2026.10.19](https://github.com/certifi/python-certifi/security/advisories/GHSA-6q48-6c7w-9gw2) |
| pip | [26.2.2](https://github.com/pypa/pip/blob/main/NEWS.rst#2622-2026-10-20) |
| sigstore | [4.5.1](https://github.com/sigstore/sigstore-python/releases/tag/v4.5.1) |
| conda | [26.9.4](https://conda.org/blog/2026-10-21-emudhra-security-updates) |
| pixi |  |
| ca-certificates | 2026.10.19 |

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5f49f24b4bbd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.