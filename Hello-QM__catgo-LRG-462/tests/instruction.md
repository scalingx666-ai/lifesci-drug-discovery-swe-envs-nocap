# Issue

**Title:** fix(docs): PDF renders via pdf.js; themed shell; Edit in header; swallow Monaco Canceled

## Description

Four doc-viewer issues from today's testing round:

## 1. PDF preview blank (desktop Linux)

`<iframe src=blob>` depends on the webview's **native** PDF renderer — WebKitGTK (Tauri's Linux webview) has none, so the frame was always empty. Replaced with **pdfjs-dist** canvas rendering: fit-to-width, devicePixelRatio-aware, one canvas per page, loading/error states. Consistent across Linux/macOS/Windows/browser.

## 2. Doc tab strip "active looks dim"

`.doc-viewer` referenced `--bg-color`, which is defined **nowhere** in the project — the shell always fell back to dark. With the app in light theme, the strip drew light-theme text (`--text-color: #374151`) on that dark surface: the active tab looked dimmer than inactive ones. Now uses the themed `--page-bg` (verified: light shell `#f1f3f5` in light theme).

## 3. markdown Edit button floating over Download

The Edit/Render toggle was an absolutely-positioned overlay on top of FilePreviewPanel's header. For markdown preview it now renders **inside the header row** (new `edit_action` prop, same `.preview-btn` styling as PDF/Download). The overlay remains only for renderers without a header (Monaco, HtmlView).

## 4. "Unhandled rejection: Canceled" error screen

Monaco cancels in-flight delayers when an editor/model is disposed (tab close, HMR). `desktop/main.ts`'s global rejection reporter runs **before** MonacoEditorPanel's `preventDefault` guard (listener registration order), so the benign `Canceled` is now filtered in `is_ignorable_runtime_error` as well.

## Verification

- Live at :3100 `#docs`: shell background follows theme; pdf.js 6.1 renders a generated test PDF to canvas with non-blank pixels through the same Vite pipeline the component uses.
- `vitest run`: 4406 pass.
- New dep: `pdfjs-dist`.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `659ff5830250`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.