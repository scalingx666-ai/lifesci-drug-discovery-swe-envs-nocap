# Issue

**Title:** #3882 – Make SVG glyph and element ids unique across renders

## Description

## Summary

Cairo's SVG backend restarts its glyph/gradient/mask/filter/pattern id counters at zero for every
document. Two or more Indigo SVGs inlined into one HTML page therefore share ids and
`xlink:href` / `url(#...)` references, and one image ends up drawn with another's glyphs.

Indigo now buffers cairo's SVG output and gives every id, and every reference to it, a per-render
prefix before writing it out.

## Changes

- New option `render-svg-unique-id` (bool, default `true`). With `false` the SVG is written exactly
  as before, byte for byte, for callers that compare or cache SVG output.
- Ids are rewritten by parsing the SVG with the existing tinyxml2 dependency
  (`core/render2d/src/render_svg_ids.cpp`): `id="x"`, `href="#x"` / `xlink:href="#x"` and `url(#x)`
  inside any attribute.
- Prefix: `i<hex>-`, where `<hex> = crc32(svg) + crc32(current time and a process-wide counter)`,
  using `CRC32` from `common`. The counter makes two identical drawings rendered at the same moment
  get different prefixes; the leading letter keeps ids valid XML names and CSS selectors.
- If cairo's output is not well-formed XML (it can write an unterminated `<image>` for an empty mask,
  seen on macOS), the SVG is returned unchanged rather than failing a render that worked before.
- SVG write errors from cairo are now reported instead of being ignored.

## Tests

- Python: ids unique within a document and disjoint between renders (molecules, file output, grids),
  every reference resolves, gradient references follow their ids, the option and its default, and
  the malformed-SVG fallback.
- The threaded C++ test and the custom-fonts integration test turn the option off, because they
  compare SVG byte for byte.

## Generic request
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name does not contain '#'
- [x] base branch (master or release/xx) is correct
- [x] PR is linked with the issue
- [x] task status changed to "In Review"
- [x] code follows product standards
- [x] regression tests updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c0c22c698bb9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.