# Issue

**Title:** Guard input dialogs against nested overwrite prompts

## Description

The "Overwrite modified input files?" message box runs a nested event loop. A molecule change or pending timer during that loop re-entered the update function and opened another box, eventually overflowing the stack. Add a re-entry guard to the input generator widget and the GAMESS, CP2K, LAMMPS and OpenMM dialogs.

Also keep an empty Title empty in the option cache, so declining the overwrite does not write the generated title into the field as text.

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

<!-- coderabbit-ai-generated:v1 -->

## Summary by CodeRabbit

* **Bug Fixes**
  * Prevented multiple overwrite-confirmation dialogs from appearing at once when updating input previews across several simulation input generators.
  * Declining an overwrite now restores the previous options, while accepting continues with the updated input.
  * Empty titles remain empty in generated input instead of being replaced with an automatically generated title.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aa2198141f73`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.