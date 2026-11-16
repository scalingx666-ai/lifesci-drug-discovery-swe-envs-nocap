# Issue

**Title:** Serialization and embedding NGLWidget + add NGLModel

## Description

[1tsu.txt](https://github.com/arose/nglview/files/1233015/1tsu.txt)
<img width="1141" alt="screen shot 2017-08-17 at 9 03 23 pm" src="https://user-images.githubusercontent.com/4451957/29439996-8a9782a0-838f-11e7-9985-6a6d35df0688.png">

How?
- In the notebook, choose "Widgets" -> "Embed Widgets" -> "Copy to Clipboard" -> open text edit, paste the context, save it to "1tsu.html"

- Open it via web browser

See attached file for example content of "1tsu.html"

@arose Please try to open it in your computer and let me know if that works for you.
(need to rename "1tsu.txt" to "1tsu.html")

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c1d85aa25708`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.