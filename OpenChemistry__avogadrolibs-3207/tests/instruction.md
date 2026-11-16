# Issue

**Title:** Fix performace-avoid-endl warnings in rendering

## Description

Takes the performace-avoid-endl, avogadro/rendering from #3101 :

## Commands
To build:
```
cmake -DQT_VERSION=6 -S avogadrolibs -B ./build -DCMAKE_EXPORT_COMPILE_COMMANDS=ON -DENABLE_TESTING=ON && cmake --build ./build -j 16
```
Applying fixes:
```
run-clang-tidy -p ../build \
  -checks='-*,performance-avoid-endl' \
  -header-filter='avogadro/rendering/' \
  -fix 'avogadro/rendering/.*\.cpp$'
git clang-format
```

Verifying that no warnings are reports for performace-avoid-endl  in rendering after application of fixes:
```
run-clang-tidy -p ../build \
  -checks='-*,performance-avoid-endl' \
  -header-filter='avogadro/rendering/' \
  'avogadro/rendering/.*\.cpp$'
```

Testing with avogadrodata cloned next to avogadrolibs:
```
ctest --test-dir ../build
```
Passed 127/127 tests.

Part of #3101.

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6aaebca7c4a5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.