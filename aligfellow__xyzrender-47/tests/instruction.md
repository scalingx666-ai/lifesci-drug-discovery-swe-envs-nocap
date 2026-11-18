# Issue

**Title:** Chemdraw style addition

## Description

## Summary

This PR adds a new `chemdraw` rendering preset and associated renderer changes to approximate a Chemdraw-style 2D line diagram, while reusing xyzrender’s existing graph and SVG pipeline.

- Introduces a `chemdraw` preset that removes atom circles, draws uniform thin bonds, and labels non‑carbon atoms with bold element symbols.
- Adjusts the renderer so Chemdraw labels use CPK colours and bonds are positioned to avoid overlapping the text, including special handling for aromatic bonds.
- Adds documentation and example figures for the new Chemdraw style (caffeine and bimp).

## Details

### Preset and configuration

- Added `src/xyzrender/presets/chemdraw.json`:
  - `chemdraw_style: true` to toggle Chemdraw-specific behaviour in the renderer.
  - White background, black bonds (`bond_width` tuned for line diagrams).
  - No gradients, fog enabled (depth cueing preserved).
  - Larger `label_font_size` for legible element symbols.
- Extended `RenderConfig` with:
  - `chemdraw_style: bool = False` (default off), set from presets/JSON via the existing config machinery.

### Atom rendering (Chemdraw mode)

- In `render_svg`:
  - When `cfg.chemdraw_style` is `True`:
    - **No atom circles** are drawn.
    - **Carbon atoms**: implied, no label.
    - **Non-carbon atoms**: drawn as bold text at the projected atom position using a sans-serif font.
      - Base colour comes from the same **CPK palette** used for standard rendering.
      - If fog is enabled, the label colour is blended with the fog colour (`blend_fog`) for consistent depth fading.
      - **Hydrogen labels** are forced to black (`#000000`) to stay visible on light backgrounds.
  - The existing index-label logic (`cfg.show_indices`) remains unchanged and is only active when explicitly requested.

### Bond rendering and placement

- **Bond endpoints**:
  - All bonds still use 3D radii to determine start/end points, then project to 2D.
  - In Chemdraw mode:
    - For **carbon atoms**, the effective radius is forced to zero so bonds meet at the carbon centre.
    - For **non-carbon atoms**, the effective radius is `max(original_radius, k * label_font_size / scale)` (with an empirical factor), so the bond endpoint moves further away from the atom as labels get larger, reducing overlap with text.

- **Uniform thickness**:
  - In Chemdraw mode, all covalent bonds (single, double, aromatic) use a **uniform, slightly thinner stroke width** (e.g. `bond_width * 0.6`), independent of bond order. This keeps the visual style consistent.

- **Aromatic bonds (special handling)**:
  - Non-Chemdraw styles retain the original behaviour: two parallel lines displaced symmetrically, with one dashed toward the ring centre.
  - In Chemdraw mode, aromatic bonds are drawn as:
    - One **solid line centred** on the bond (no perpendicular offset), visually like a single bond.
    - One **dashed line**:
      - Offset further toward the ring centre using the perpendicular direction `(px, py)` and `gap`.
      - **Shortened** at both ends by trimming a fraction of the bond length along the bond direction, so it doesn’t run into atom labels or other bonds.
    - Both components use the uniform Chemdraw stroke width.

### Documentation and examples

- `README.md`:
  - Updated the **Presets** table to include a Chemdraw-style column with `examples/images/caffeine_chemdraw.svg`.
  - Added a CLI example:
    ```bash
    xyzrender caffeine.xyz --config chemdraw -o caffeine_chemdraw.svg
    ```
- Example images:
  - `examples/images/caffeine_chemdraw.svg` and `examples/images/bimp_chemdraw.svg` generated with the new preset.

## Future work / known limitations

This PR focuses on the core Chemdraw-like look (hidden C–H, labelled heteroatoms, uniform thin bonds, aromatic styling, CPK-coloured labels). There are still several refinements that could be tackled in follow-up PRs:

- **Double/triple bond layout**:
  - Current Chemdraw mode keeps multiple lines but does not yet optimize spacing/length per bond order to match Chemdraw conventions (e.g. inside vs outside bonds, asymmetric placement).
  - Refining these layouts—especially around heteroatoms and in crowded aromatic systems—would further improve readability.

- **More precise label–bond interaction**:
  - The current label clearance is based on a simple mapping from font size to effective radius.
  - A more geometry-aware solution (e.g. using measured text extents or adaptive trimming per bond/label pair) could reduce edge cases where long labels are close to bonds.

- **Additional presets / variations**:
  - Variants for black-and-white export (no CPK colours), or thinner stroke widths for dense structures, could be added as separate presets built on top of this Chemdraw mode.

I’m happy to iterate on any of these in subsequent PRs if you’d like to refine the Chemdraw style further.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9a65f4ec7f8e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.