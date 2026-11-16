# Issue

**Title:** Register obmm force fields only when obmm is available

## Description

Without BUILD_GPL_PLUGINS, the MMFF94 and GAFF models were always registered and ran an external obmm binary. If obmm was not installed, starting the process only logged a debug message, energies were returned as 0.0, and optimizations reported convergence.

Add OBMMEnergy::isAvailable(), check, and then use qDebug if missing

Developer Certificate of Origin
Version 1.1

Copyright (C) 2004, 2006 The Linux Foundation and its contributors.
1 Letterman Drive
Suite D4700
San Francisco, CA, 94129

Everyone is permitted to copy and distribute verbatim copies of this
license document, but changing it is not allowed.

Developer's Certificate of Origin 1.1

By making a contribution to this project, I certify that:

(a) The contribution was created in whole or in part by me and I
    have the right to submit it under the open source license
    indicated in the file; or

(b) The contribution is based upon previous work that, to the best
    of my knowledge, is covered under an appropriate open source
    license and I have the right under that license to submit that
    work with modifications, whether created in whole or in part
    by me, under the same open source license (unless I am
    permitted to submit under a different license), as indicated
    in the file; or

(c) The contribution was provided directly to me by some other
    person who certified (a), (b) or (c) and I have not modified
    it.

(d) I understand and agree that this project and the contribution
    are public and that a record of the contribution (including all
    personal information I submit with it, including my sign-off) is
    maintained indefinitely and may be redistributed consistent with
    this project or the open source license(s) involved.

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

* **Bug Fixes**
  * MMFF94 and GAFF force-field models are now available only when the OBMM executable can be found, avoiding unavailable model options.
  * OBMM discovery now checks a configured executable, an application-bundled executable, and the system PATH. Bundled setups use matching Babel data and library paths when available.
* **Tests**
  * Added checks for OBMM executable discovery and force-field availability.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `76490fbe3771`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.