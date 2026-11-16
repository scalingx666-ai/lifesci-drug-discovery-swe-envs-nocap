# Issue

**Title:** Keep unique ids when undoing a molecule replacement

## Description

Thanks to Claude Opus 5.5 for catching this bug (through a new fuzz test) The fuzzer found it with removeBonds -> wrapUnitCell -> undo -> undo -> redo: the second undo gave the wrong bonds and the redo lost one more.

QtGui::Molecule keeps unique-id tables (unique id -> index, with MaxIndex holes for deleted items), and the undo commands in rwmolecule_undo.h refer to atoms and bonds by unique id. operator=(const Molecule&) copies those tables, but the copy constructor renumbers them 0..n-1.

ModifyMoleculeCommand stored the live molecule with the copy ctor so undo put back a molecule with different unique ids!

The old molecule now keeps the live molecule's tables (default construct, then operator=). The new molecule still goes through the copy constructor on purpose: callers build it by editing a copy through Core-level functions (CrystalTools re-perceiving bonds, building a supercell), which change atoms and bonds without updating the QtGui tables, so they may be stale. Renumbering makes them consistent with the new molecule's counts.

The underlying trap is the copy constructor / operator= asymmetry, which is left alone here; worth fixing properly for 2.2.

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
  * Improved undo and redo reliability when editing molecules after atoms or bonds have been removed, preserving the correct atoms, bonds, positions, and IDs.
  * Fixed undo and redo behavior for sequences involving bond removal and wrapping atoms into the unit cell, so molecular structures and atom positions are restored and reapplied correctly.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3f9cd1106b39`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.