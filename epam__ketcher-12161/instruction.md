# Issue

**Title:** #4669 - Preview: When saving in SVG file format from Text-editing mode, a pink highlight is displayed on the preview and the cursor blinks

## Description

## How the feature works? / How did you fix the issue?
(Screenshots, videos, or GIFs, if applicable)
<img width="959" height="491" alt="aassaaa" src="https://github.com/user-attachments/assets/e0f73da8-85aa-4bbb-b5f4-5e74ca2640ba" />

## What
SVG (and PNG) export from Sequence text-editing mode no longer includes the blinking caret and the "▷" chain-start arrow. The pink edit-mode cell background from the original report no longer appears on master (the background is created transparent and nothing recolours it).

## Why
The export (`getSvgFromDrawnStructures`) removes every `.dynamic-element` — the marker other renderers put on hover, selection and attachment-point visuals. The sequence caret group and the start arrow, both edit-mode-only, didn't carry it, so they ended up in the image. The issue's requirement: temporary objects (cursor, selectors, …) must not be included.

## How
`BaseSequenceItemRenderer` adds `class="dynamic-element"` to the caret group (`showCaret`) and to the start-arrow `<use>` (`appendChainStartArrow`). The canvas is unchanged; only exports drop them. The export viewBox is measured from the live canvas, so the image framing stays the same.

## Verification
- Reproduced on master and checked with the fix in the browser: the SVG preview from text-editing mode shows only the letters and counter; the canvas still shows the caret and arrow while editing; view-mode export unchanged.
- New test in `SequenceRenderer.test.ts` renders a sequence in edit mode with the caret and checks the exported SVG has neither the caret nor the arrow; it fails on master.
- Docker run of the Macromolecules export specs (`import-saving-idt.spec.ts`, popup `ketcher-3.13.0-bugs.spec.ts`) passes with no screenshot changes.
- `npm run test` and `npm run test:types` pass.

## Check list
- [ ] unit-tests written
- [ ] e2e-tests written
- [ ] documentation updated
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name doesn't contain '#'
- [x] PR is linked with the issue
- [ ] base branch (master or release/xx) is correct
- [x] task status changed to "Code review"
- [ ] reviewers are notified about the pull request

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6fb746d04f86`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.