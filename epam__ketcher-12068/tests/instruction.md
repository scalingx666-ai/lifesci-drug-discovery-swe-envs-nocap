# Issue

**Title:** #7199 - Ruler slider becomes locked when dragged beyond canvas edge

## Description

## How the feature works? / How did you fix the issue?
(Screenshots, videos, or GIFs, if applicable)
## What
While the ruler slider is dragged past an edge of the visible canvas, the canvas scrolls so the slider stays on screen and can be grabbed again. This follows the decision in the issue comments ("scroll canvas to keep caret always visible").

## Why
The input next to the slider was kept inside the visible area, but the slider itself never was. A drag that ended beyond the edge left the slider off-screen with no way to grab it, so only typing a number got it back.

## Behaviour
- While dragging: if the slider and its input would cross the right or left visible edge, the canvas scrolls by the overshoot. The line length still follows the mouse; scrolling doesn't change the value.
- On release: Sequence mode snaps the value to a multiple of 10, which can land past where the slider was dragged. The same check runs for the snapped position.
- On the left, the canvas never scrolls the start of the ruler past the edge.
- Unchanged: typing a value. When a typed value puts the slider outside the viewport, the input still moves to the corner (#6738 §5, ruler Case 11).

## Verification
- Unit tests in `RulerArea.test.tsx`: dragging past the edge scrolls, dragging inside the visible area doesn't, and a release that snaps past the edge scrolls. The first fails on master; the third fails without the release check.
- Checked in the browser in Sequence and Snake mode, at 100% and 50% zoom.
- `ruler.spec.ts` and the ruler cases in the 3.5.0/3.6.0 bug specs pass in Docker, with no screenshot changes.
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b0019f70e47`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.