# Issue

**Title:** Use NGL .2.1.1 for nbclassic and VSCode

## Description

- delete original `nglview/static` folder  (this folder is for nbclassic (and thus, VSCode)
- Update NGL version to 2.1.1 https://github.com/nglviewer/nglview/blob/668abf9c952f93b981f0b480477a81c4c5d7218b/js/package.json#L81
- NGL 2.1.1 is the latest "working" version (included in `nglview` v3.0.8). Details is in  (NGL 2.2.1 doesn't work either)
- `npm install` and commit the new changes for `static` folder. 
- Restore the change for `package.json`

<img width="1436" alt="image" src="https://github.com/user-attachments/assets/7e1e8473-fc10-4b0a-a4f3-08664b59efd9">

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `668abf9c952f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.