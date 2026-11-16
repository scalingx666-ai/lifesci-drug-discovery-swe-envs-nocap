# Issue

**Title:** feat(web): Implement Global File Dropzone Overlay

## Description

### Summary:

Introduced a `GlobalDropzone` component that creates a full-screen overlay when users drag files anywhere over the application window. This provides a consistent and reliable target for file uploads, improving usability compared to restricting drops to specific zones. The implementation includes state management to correctly handle drag enter/leave events across child elements, preventing flickering.

### Changes:

- **Created `GlobalDropzone` Component:**
  - Implemented a full-screen overlay using `framer-motion` for smooth enter/exit animations.
  - Developed a custom `useGlobalDragState` hook to robustly track drag events, using a counter to handle event bubbling from child elements without premature dismissal.
  - Added support for filtering files by extension using the shared `filterFiles` utility.

- **Integrated into `AppLayout`:**
  - Wrapped the main application layout with `GlobalDropzone`, enabling drag-and-drop uploads from any view within the app.
  - Connected the drop handler to the existing `useFileUpload` hook for seamless processing.

- **Refactored `Dropzone` Pattern:**
  - Exported `filterFiles` from the base `Dropzone` component to share validation logic.
  - Updated the `ui/patterns` export barrel to include the new global component.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `79bb1d8923d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.