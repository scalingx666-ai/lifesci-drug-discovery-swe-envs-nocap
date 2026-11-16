# Issue

**Title:** Fix TypeError when getOverlay() returns None with no particles

## Description

`imagej2_analyze_particles_binary_jython_script.py` crashes with:
```
TypeError: 'NoneType' object is not iterable
```
at the line:
```python
for i, roi in enumerate(ov):
```
whenever `export_rois=true` and **zero particles** match the analysis criteria
(e.g. `size=50-Infinity` on an image whose binary mask has no blob ≥ 50 px²).

Root cause: `ImagePlus.getOverlay()` returns `None` (not an empty list) when
Analyze Particles produces no results. The script then tries to iterate over
`None`, which raises `TypeError`.

This is the real failure underlying Step 14 (`Generate ROIs of stained region`)
in the IWC histological staining workflow PR
]().

## Fix

One-line change in `imagej2_analyze_particles_binary_jython_script.py`:
```python
# Before
ov = input_image_plus_copy.getOverlay()

# After
ov = input_image_plus_copy.getOverlay() or []
```

## Changes

- `imagej2_analyze_particles_binary_jython_script.py`: guard `getOverlay()` against `None`
- `imagej2_analyze_particles_binary.xml`: add regression test for zero-particles case
- `test-data/analyze_particles_rois_empty.tabular`: expected header-only output for the new test

## Test case added

```xml
<test expect_num_outputs="2">
    <param name="input" value="blobs.gif"/>
    <param name="size" value="100000-Infinity"/>
    <param name="show" value="Nothing"/>
    <param name="export_rois" value="true"/>
    <output name="results" file="analyze_particles_nothing.tabular"/>
    <output name="rois" file="analyze_particles_rois_empty.tabular"/>
</test>
```

`analyze_particles_rois_empty.tabular` contains only the header row:
```
shape	points	label	t	z
```
@mvdbeek

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dd275a3e8606`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.