# Issue

**Title:** Guard the settings widget pointer in scene layer data

## Description

The ball-and-stick, cartoon, label, licorice, van der Waals and wireframe layer data each held a raw QWidget* to their settings panel and called deleteLater() on it when destroyed.

Hold the widget in a QPointer so the destructor only deletes it if it is still alive. Ownership is unchanged: the layer data still cleans up a panel nobody else took, and clone() still does not share it.

Regression tests for each of the six create the panel, delete it, and destroy the molecule (all crashed before), and check an unclaimed panel is still deleted with the layer data.

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
  * Improved stability when layer panels are closed before related scene data is cleared, preventing failures during cleanup.
* **Tests**
  * Added regression coverage for layer-panel cleanup, including cases where panels are closed early or remain unclaimed.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c2e6620eb455`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.