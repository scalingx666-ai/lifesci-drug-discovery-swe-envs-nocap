# Issue

**Title:** New Tool Coco2Labelme

## Description

- [x] I have read the [CONTRIBUTING.md](https://github.com/galaxyproject/tools-iuc/blob/master/CONTRIBUTING.md) document and this tool is appropriate for the tools-iuc repo.
- [x] License permits unrestricted use (educational + commercial)
- [x] This PR adds a new tool or tool collection
- [ ] This PR updates an existing tool or tool collection
- [ ] This PR does something else (explain below)

---

This tool converts COCO annotation files (JSON) into LabelMe JSON files, one per image.

The SAM3 export creates results in COCO format. However, if you want to check or fix the annotations by hand using AnyLabeling, you cannot do this because AnyLabeling needs the LabelMe JSON format

### Notes

- The code is based on [cv_utils by WoodsGao](https://github.com/WoodsGao/cv_utils) (GPL-3.0). This tool is also released under GPL-3.0.
- The user can choose how the `imagePath` field is written in the output, to match different folder structures (simple, AnyLabeling default, or custom path).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0b056563af03`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.