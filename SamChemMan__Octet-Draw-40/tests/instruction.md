# Issue

**Title:** Normalise line endings to LF, so the checks pass on a Windows clone

## Description

59 of the 99 check files read Octet's own source and match it against patterns written with `\n`. Git's default on Windows is `core.autocrlf=true`, so a clone there gets CRLF in the working tree and **five checks fail before anything has been changed**:

```
FAIL src/cursor.check.ts
FAIL src/filesafety.check.ts
FAIL src/pagefit.check.ts
FAIL src/projects.check.ts
FAIL src/purpose.check.ts
94 of 99 check files pass.
```

They are not real failures. `cursor.check.ts` gives it away — it expects `\nif (typeof document !== "undefined") drawCursors();\n` and the file it reads ends its lines with `\r\n`.

This adds a `.gitattributes` with `* text=auto eol=lf`, which normalises the working tree on every platform.

**Before:** 94 of 99 on a fresh Windows clone.
**After:** 99 of 99. Nothing changes on macOS or Linux, where the files were already LF.

No file in the repository needs CRLF. The only Windows script, `scripts/drive/windows.ps1`, is read by PowerShell, which does not care either way.

### Why it is worth a patch rather than a note

It is invisible from a Mac, and it lands on the first thing a new Windows contributor does. Someone cloning the repository to try a fix sees five failing tests and has no reason to suspect their own checkout — the natural conclusion is that `main` is broken.

I found it setting up to work on some of the Windows issues I filed earlier today (#32, #33, #25, #31), on Windows 11 with Node 24.22.2.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f11487e97ee3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.