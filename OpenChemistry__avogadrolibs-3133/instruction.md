# Issue

**Title:** Use new-style connections in bonding plugin

## Description

Part of #3100: converts the 7 SIGNAL/SLOT connections in `qtplugins/bonding` to new-style function-pointer connections, so they are checked at compile time. No behavior change intended.

`git grep -E "SIGNAL\(|SLOT\(" avogadro/qtplugins/bonding` now returns nothing.

### Testing (Linux / WSL, Qt 6.10)
Opened the running app and tried every control whose connection changed:
- Build → Bond → Bond Atoms (menu and Ctrl+B): bonds created
- Build → Bond → Bond Selected Atoms: bonds created only between selected atoms
- Build → Bond → Perceive Bond Orders: runs, shows in Edit → Undo
- Build → Bond → Remove Bonds (menu and Ctrl+Shift+B): bonds removed
- Build → Bond → Configure Bonding…: OK saves tolerance / minimum distance; Cancel closes the dialog without saving (same as before)

---

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

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a4ff1e055a33`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.