# Issue

**Title:** Add DCD fuzz target with small generated seeds

## Description

Fuzz the DCD reader in CI as dcd=dcd-small. The only DCD in avogadrodata is a 1 MB trajectory, which would inflate libFuzzer's max_len and slow every run, so the seeds live in tests/io/fuzz/dcd-small/, written by generate_dcd_seeds.py. They cover X-PLOR and CHARMM headers, the unit cell and fourth-dimension records, fixed atoms, both byte orders, and a truncated last frame. A small dictionary holds the record markers.

fuzz_windows.yml only read seeds from avogadrodata, so teach it the in-repo seed directory and .dict lookup that fuzz_linux.yml already has.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9d2307b4bc4e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.