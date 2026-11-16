# Issue

**Title:** Drop unused SimDivPickers dependency from SynthonSpaceSearch

## Description

#### Reference Issue
Same failure as #9437 (fixed for GaussianShape in #9438), this time in SynthonSpaceSearch.

#### What does this implement/fix? Explain your changes.
SimDivPickers isn't built when `RDK_BIG_ENDIAN` is set, but SynthonSpaceSearch lists it in its link libraries, so on big-endian hosts the build stops with:

```
ld.lld: error: unable to find library -lSimDivPickers
```

The dependency came in with the synthon space shape search (#9279) together with an `#include <SimDivPickers/LeaderPicker.h>` in `SynthonSpaceSearch_details.cpp`, but nothing in SynthonSpaceSearch uses a picker. The only LeaderPicker user is `ShapeInput::pruneShapes()` in GaussianShape. This removes the unused include and the link dependency. Little-endian builds still get SimDivPickers through GaussianShape's public link interface, so nothing changes there.

Seen on FreeBSD/powerpc64 (big-endian) with 2026_03_6. With this change the full build (Python wrappers on) completes there.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c285b8984b49`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.