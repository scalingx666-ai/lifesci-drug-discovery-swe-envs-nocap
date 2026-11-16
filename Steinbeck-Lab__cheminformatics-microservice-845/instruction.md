# Issue

**Title:** feat: add Docling PDF text extraction endpoints

## Description

Port the 2025 dev-docling work onto current development and fix it:

- Convert uploads in memory with DocumentStream and page_range, so no file is written to disk and the client filename is never used as a path. The old code reused any stored PDF with the same name, which could return another user's document.
- Reject files over 10 MB and files without a %PDF- header; cap pages at 20 and rate limit both routes to 5/minute.
- Stop one conversion after 120 s (Docling document_timeout) and return 503 when the converter stays busy for 30 s.
- Respect the pages field in /tools/extract_json (it was hardcoded to 3).
- Read page numbers from prov[].page_no and the "title" label, which is what Docling 2.x exports (page_number and font_size do not exist).
- Drop PyPDF2; the first-page fallback now uses Docling's own output.
- Load the converter once and run the blocking work in sync routes.
- Register the routes only when docling is installed, so the lite image works without it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4be2b07c213d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.