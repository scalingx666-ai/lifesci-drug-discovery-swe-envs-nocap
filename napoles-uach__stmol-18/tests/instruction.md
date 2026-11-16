# Issue

**Title:** ♻️ Restructuring the Folders

## Description

Hi @napoles-uach , this pull request deals with organizing the folders primarily, 
- Major pushes are related to this commit - 8fec369e4066025d213e71ef478b0e830d40c8d5
  - 🎨 Added a Resources Folder for images, gifs etc and pushed your demo gif there
  - 🔒 `build/lib/stmol` directory was removed, and added that in `.gitignore`
  -  🎉 `tests/example-stmol-speck.py` is added . This folder can be renamed as `Pages` for the MultiPage Streamlit App, which we plan to put up as an example App 
  -  ⚠️ `sub0.py` file is removed from the root , is that necessary ? 
  - ⚠️ `setup.py` is added with `speck` dependencies  - >`"ipyspeck==0.6.1" "ipywidgets==7.6.3"`  
- ❇️   be4261d58cf7f72a10c474d67fa3fbc1c692b9db isn't critical, only updates the readme with the path of the demo.gif

If you feel like these are necessary for time being , feel free to append 🎈 🎆

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1dd08f042011`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.