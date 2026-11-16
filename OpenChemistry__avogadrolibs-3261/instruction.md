# Issue

**Title:** Find the RPC socket in the private per-user directory

## Description

Avogadro now keeps its RPC socket in $XDG_RUNTIME_DIR or <tmp>/avogadro-<uid> on Linux and BSD instead of the shared /tmp. Add avogadro.connect.socket_path() with the same resolution, and use it in connect().

The per-user directory must be a real directory owned by the user with no group/other access, otherwise the client refuses to connect. For Avogadro 2.1 and older, which still listen on <tmp>/<name>, fall back to that legacy path only when it is a socket owned by the current user; a squatter cannot create a file owned by us. macOS and absolute names are unchanged.

The fake RPC server binds where the client looks, and the resolver has tests.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f26b9d079974`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.