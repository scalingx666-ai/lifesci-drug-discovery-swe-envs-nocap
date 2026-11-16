# Issue

**Title:** Check that AppImage programs run without LD_LIBRARY_PATH

## Description

Avogadro now removes the AppImage's libraries from LD_LIBRARY_PATH for child processes, so bundled programs and Open Babel plugins must find their libraries through RUNPATH alone. Fail the AppImage job if ldd reports missing libraries, or if obabel cannot load a plugin that needs libinchi. AppRun also exports APPDIR for extracted AppDirs.

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
  * Improved reliability of Linux AppImage builds by checking that bundled components can run without relying on external library paths.
  * Added a chemistry calculation check during packaging to verify that the included Open Babel tool produces the expected ethanol result.
  * Ensured the AppImage environment is available to child processes, including when running from an extracted application directory.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `74722452b1b3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.