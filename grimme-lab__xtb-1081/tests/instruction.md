# Issue

**Title:** Make DFTD4 & multicharge dependencies optional

## Description

In this  DFTD4 and multicharge were added as dependencies for xTB. As far as I can tell, these dependencies aren't currently used (all unittests pass without them, as well as a variety of individual calculations that I have tried).

If the intention is to eventually have DFTD4 and multicharge be required dependencies, this isn't toggling isn't strictly needed, but is nice to have in the interim until features that use that use these  dependencies are added. 

My motivation for making the pull request was that I hit a build failure on Windows (ifort/msvc compilers) trying to compile the multicharge dependency:
```
[stdout] [238/690] Compiling Fortran object subprojects/multicharge/test/tester.exe.p/test_wignerseitz.f90.obj
[stdout] [239/690] Compiling Fortran object subprojects/dftd4/dftd4-3.dll.p/src_dftd4_data.f90.obj
[stdout] [240/690] Compiling Fortran object subprojects/dftd4/dftd4-3.dll.p/src_dftd4_utils.f90.obj
[stdout] [241/690] Compiling Fortran object subprojects/multicharge/app/multicharge.exe.p/main.f90.obj
[stdout] [242/690] Linking target subprojects/multicharge/app/multicharge.exe
[stdout] FAILED: subprojects/multicharge/app/multicharge.exe
[stdout] "xilink.exe"  /MACHINE:x64 /OUT:subprojects/multicharge/app/multicharge.exe subprojects/multicharge/app/multicharge.exe.p/main.f90.obj "/nologo" "-STACK:16777216" "subprojects/multicharge/multicharge.lib" "subprojects/mctc-lib/libmctc-lib.a" "subprojects/json-fortran-8.2.5/libjsonfortran.a" "mkl_rt.lib" "/SUBSYSTEM:CONSOLE"
[stdout] LINK : fatal error LNK1181: cannot open input file 'subprojects\multicharge\multicharge.lib'
```

I assume this is a similar issue to  where some symbols need to be exported in a Windows specific way. But I didn't want to dig too deep into the issue until I was sure that multicharge was actually being used by xTB.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ec4f3887e143`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.