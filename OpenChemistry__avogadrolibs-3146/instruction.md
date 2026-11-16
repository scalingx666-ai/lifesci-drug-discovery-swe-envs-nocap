# Issue

**Title:** Stop re-prompting for plugin installs that failed

## Description

installPackages() registered every package whether or not pixi/pip succeeded, and the dialog always said "Installation complete.". On the next launch scanDirectory() found no environment and offered the same failing install again (forever)

Installs now report per-package outcomes (new packageInstalled and packageInstallFailed signals; packagesInstalled still fires at the end), with the backend and tail of stderr as the message. Failed packages are not registered. The failed pyproject.toml hash is recorded under pluginInstallFailures/<dir>, apart from plugins/, so scanDirectory() skips it until the file changes; Manage Plugins still retries. A pixi failure with a working pip .venv is recorded the same way. A failed update keeps a registration only while an environment can still run it.

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

* **New Features**
  * Package installation now reports success or failure for each package, including diagnostic details when installation fails.
  * Recorded failures can be cleared to allow another installation attempt.

* **Bug Fixes**
  * Packages that fail to install are no longer automatically retried while their configuration remains unchanged; updating it allows another attempt.
  * Previously installed packages remain available after a failed update when their existing environment can still run them.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5f4f0490ab95`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.