# Issue

**Title:** Report specific RPC failures and add headless colormaps in ApplyColors

## Description

Update handleCommand() in the ApplyColors plugin so known colormap and color commands that cannot run emit commandFailed() with a specific message instead of returning false. Unknown commands still return false so routing is unchanged.

Null molecules now report "No molecule"; molecules without atoms report "Molecule has no atoms", and distance coloring validates that 3D coordinates exist. Colormap options are normalized (case-insensitive, hyphens/underscores ignored) and unknown colormaps report a specific error with Levenshtein typo suggestions when a close match exists. Charge coloring validates requested models or falls back to the first available model, reporting an error if no models exist.

Headless overloads are added for applyIndexColors(), applyDistanceColors(), and applyChargeColors(), decoupling execution logic from interactive GUI dialogs so JSON-RPC calls execute without modal popups. Unit tests in tests/qtplugins/applycolorstest.cpp verify registration, error reporting, typo suggestions, and headless execution, matching the pattern established in the Select plugin.

Addresses #2982

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cb0e94852889`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.