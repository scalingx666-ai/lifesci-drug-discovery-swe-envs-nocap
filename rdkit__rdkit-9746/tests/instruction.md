# Issue

**Title:** sping PDF: fix two error messages that raised KeyError

## Description

#### Reference Issue
None; found with a static check (ruff F523/F524, `str.format` placeholder mismatch).

#### What does this implement/fix? Explain your changes.

Two error messages in `rdkit/sping/PDF/pdfgen.py` mixed `%` placeholders with `str.format`:

- `Canvas.readJPEGInfo`: `' Unsupported JPEG marker: {%0.2x}'.format(x[0])`
- `Canvas.setPageTransition`: `'Unknown Effect Name "{%s}"'.format(effectname)`

`str.format` reads `{%0.2x}` / `{%s}` as fields named `%0` / `%s`, so building the message raised `KeyError: '%0'` / `KeyError: '%s'` instead of the intended `PDFError`. Both now use `%` formatting:

| call | before | after |
|---|---|---|
| `canvas.setPageTransition("NoSuchEffect")` | `KeyError: '%s'` | `PDFError: Unknown Effect Name "NoSuchEffect"` |
| `canvas.readJPEGInfo(...)` on a JPEG with an SOF3 marker | `KeyError: '%0'` | `PDFError:  Unsupported JPEG marker: c3` |

#### Any other comments?

I checked both cases with a small script that loads `rdkit.sping.PDF.pdfgen` from the source tree (the module is pure Python) and calls the two methods, before and after the change. I didn't add a unit test because the `sping` tests don't seem to be registered with ctest; happy to add one if there is a place it would run.

*I used Claude (an AI assistant) to help find and fix this; I reviewed the change and ran the check above.*

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `01c1ff50e7ae`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.