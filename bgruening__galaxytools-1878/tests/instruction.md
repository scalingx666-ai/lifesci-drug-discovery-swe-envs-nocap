# Issue

**Title:** New tool : Coco Visualizer

## Description

## Features

- Draws bounding boxes, segmentation masks, and labels from a COCO JSON file
- Color mode: per category or per instance
- Output: annotated frames (PNG or JPEG), a compiled MP4 video, or both
- Optional category filter to display only selected classes

## Tests

- Test 1: single image, frames output, JPEG format
- Test 2: four images, video output, per-instance color mode

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6b0798051350`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.