# Issue

**Title:** Fix RTL mirroring in Band and XRD dialogs

## Description

.

Remove explicit layoutDirection properties from the Band and XRD dialogs
so their widgets inherit the interface direction.

Replace the Plot Fermi and Zero Fermi captions with buddy labels and
textless checkboxes in the existing QGridLayout. This preserves the
text-before-box arrangement in LTR and allows it to mirror in RTL.
Keep the Zero Fermi label's enabled state synchronized with its checkbox.

Validation on Windows with Qt 6.8.3:
- Checked dialog previews in normal and reversed directions.
- Compiled both .ui files with uic.
- Checked generated and dynamically loaded interfaces for layout,
  buddy associations, enabled-state changes, and Space-key toggling.
- Completed a full Release build on Windows x64 with MSVC 19.41
  and Qt 6.8.3, including the Yaehmop and PlotXrd plugins.
- Ran the complete avogadrolibs CTest suite: 124/124 tests passed.
- Verified application startup, loading an H2O molecule, and
  exporting a rendered PNG.

AI assistance: Used ChatGPT/Codex for guidance, UI edits, debugging,
and local validation.

Screenshots:
Qt Designer editor views, shown in LTR and RTL (-reverse).
Band — LTR
<img width="458" height="317" alt="band" src="https://github.com/user-attachments/assets/9db477ce-2276-4bf3-a4d3-56e477de653f" />
Band — RTL (-reverse)
<img width="489" height="340" alt="band-reverse" src="https://github.com/user-attachments/assets/c283a613-b156-447e-b6c5-11fdcf68e844" />
XRD — LTR
<img width="249" height="191" alt="XRD" src="https://github.com/user-attachments/assets/ee0a133b-6c73-475f-8f7d-1b6cbbe09a48" />
XRD — RTL (-reverse)
<img width="290" height="220" alt="XRD-reverse" src="https://github.com/user-attachments/assets/e2b72464-42df-478d-b47c-2a3c9555e429" />

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7da869102895`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.