# Issue

**Title:** Fix psi4 windows version detection

## Description

<!-- Thank you for your contribution! -->

## Description
psi4 on windows was computing lovely stuff like the below, so clearly the `.split()[-1]` that I removed in #418 was needed. The new check that stdout isn't empty should avert trouble with the split. And stdout is a string in util.popen(), so the strip() should be safe.
```
+#2023-08-17T20:15:44.6106581Z [1m[31mE   pkg_resources.extern.packaging.version.InvalidVersion: Invalid version: '-D-a-psi4-psi4-objdir-C-Miniconda3-envs-baseenv-python.exe.D-a-psi4-psi4-objdir-stage-bin-psi4.-version.-1.9a1.dev42'[0m
+#2023-08-17T20:15:44.6107842Z ------------------------------- Captured stdout -------------------------------
+#2023-08-17T20:15:44.6108602Z found (no psithon) exc["proc"].returncode=0 so='D:\\a\\psi4\\psi4\\objdir\\stage\\bin\\psi4\r\n' se=''
+#2023-08-17T20:15:44.6109594Z get_version exc["proc"].returncode=0 exc["stdout"]='\r\nD:\\a\\psi4\\psi4\\objdir>C:/Miniconda3/envs/baseenv/python.exe D:\\a\\psi4\\psi4\\objdir\\stage\\bin\\psi4 --version \r\n1.9a1.dev42\r\n' exc["stderr"]=''
```


## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1a36ef7ccaea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.