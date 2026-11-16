# Issue

**Title:** Add per-plugin smoke tests found through the PluginManager

## Description

One gtest test per plugin and kind of check, registered from whatever the PluginManager finds, so a new plugin is covered the day it is added:

  PluginSmoke/Extension  construction, names, actions, menu paths,
                         commands and schemas, every molecule fixture
  PluginSmoke/Actions    every enabled action triggered on every fixture
                         with modal dialogs dismissed; plugins that reach
                         the network or an external program are skipped
  PluginSmoke/Scene      process() and processEditable() on every fixture
  PluginSmoke/Tool       a fixed tour of mouse, wheel and key events
                         through a GLWidget, then undo back to the start

Each ends with the CommandTestHarness molecule invariants. They ask whether a plugin survives and stays consistent, not whether the chemistry is right. (That's for future tests.)

Qt dialogs are widget-based (AA_DontUseNativeDialogs) so the dismisser can close them; a watchdog thread ends the run, naming the action, if one stays blocked for 30 s instead of hanging it.

Plugins that build text labels (scene Label and several tools) skip without an OpenGL context rather than crash; see haveGLContext().

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

* **Tests**
  * Expanded automated smoke-test coverage across extensions, actions, scene plugins, and tools using a range of molecular data.
  * Tests now check plugin behavior, molecule integrity, and undo restoration, while handling plugins that require unavailable graphics or interact outside the application.
  * Added separate test runs for each plugin category.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b9ed29b0578c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.