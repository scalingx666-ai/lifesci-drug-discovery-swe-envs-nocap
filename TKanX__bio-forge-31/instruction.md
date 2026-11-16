# Issue

**Title:** fix(web): Prevent File Card Expansion When Selecting Files

## Description

### Summary:

Fixed a UI interaction issue in the `FileCard` component where clicking the selection checkbox would incorrectly trigger the card's expansion logic. This was caused by the click event bubbling up to the parent container. The fix involves wrapping the checkbox in a dedicated container that explicitly stops event propagation, ensuring that selection and expansion actions remain independent.

### Changes:

- **Updated `FileCard.tsx`:**
  - Wrapped the `Checkbox` component within a `div` element.
  - Moved the `e.stopPropagation()` logic to the `onClick` handler of this wrapper `div`.
  - This ensures that clicks on the checkbox (or its label area) do not bubble up to the card's main click handler, preventing unwanted expansion/collapse toggling.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `79bb1d8923d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.