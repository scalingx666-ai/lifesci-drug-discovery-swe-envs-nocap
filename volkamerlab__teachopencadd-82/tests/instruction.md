# Issue

**Title:** T015 - Protein-ligand docking

## Description

# Details

* Talktorial ID: 015
* Title: Protein ligand docking
* Original authors: Jaime Rodríguez-Guerra, Dominique Sydow
* Reviewer(s): Jaime Rodríguez-Guerra
* Date of review: Dec 2020 - ...

# Content review

* Potential labels or categories (e.g. machine learning, small molecules, online APIs): XXXXXXXX
* One line summary: Dock small molecules into a protein.
* [x] The table of contents reflects the talktorial story-line; order of #, ##, ### headers is correct
* [x] URLs are linked with meaningful words, instead of pasting the URL directly or linking words like `here`.
* [x] I have spell-checked the notebook
* [x] Images have enough resolution to be rendered with quality, without being _too_ heavy.
* [x] All figures have a description
* [x] Markdown cell content is still in-line with code cell output (whenever results are discussed)
* [x] I have checked that cell outputs are not incredibly long (this applies also to `DataFrames`)
* [x] Formatting looks correctly on the Sphinx render (bold, italics, figure placing)

# Code review

* Time it took to execute (approx.):
* [x] Variable and function names follow snake case rules (e.g. `a_variable_name` vs `aVariableName`)
* [x] Spacing follows PEP8 (run Black on the code cells if needed)
* [x] Code line are under 99 characters each (run `black -l 99`)
* [x] Comments are useful and well placed
* [x] There are no unpythonic idioms like `for i in range(len(list))` (see slides)
* [x] All 3rd party dependencies are listed at the top of the notebook
* [ ] I have marked all code cell with output referenced in markdown cells with the label `# TODO: CI`
* [ ] I have identified potential candidates for a code refactor / useful functions
* [x] All `import ...` lines are at the top (practice part) cell, ordered by standard library / 3rd party packages / our own (`teachopencadd.*`)
* [x] I have update the relative paths to absolute paths.
* List here unfamiliar libraries you find in the imports and their intended use:

# Other
* [x] integrate [Michele's version](https://github.com/MicheleWichmann/TeachOpenCADD/blob/t11-ifp/talktorials/11_online_apis/11b_online_docking.ipynb)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2ecfe7216773`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.