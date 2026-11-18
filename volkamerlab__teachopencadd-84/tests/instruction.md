# Issue

**Title:** T011 - Querying online API webservices

## Description

<!-- Talktorial review template -->
<!-- Thank you very much for helping us improve TeachOpenCADD! -->

# Details

* Talktorial ID: T011
* Title: Querying online API webservices
* Original authors: Jaime Rodríguez-Guerra
* Reviewer(s): David Schaller
* Date of review:

# Content review

* Potential labels or categories (e.g. machine learning, small molecules, online APIs): XXXXXX
* One line summary: XXXXXXXXXX
* [x] The table of contents reflects the talktorial story-line; order of #, ##, ### headers is correct
* [x] URLs are linked with meaningful words, instead of pasting the URL directly or linking words like `here`.
* [ ] I have spell-checked the notebook
* [x] Images have enough resolution to be rendered with quality, without being _too_ heavy.
* [ ] All figures have a description
* [x] Markdown cell content is still in-line with code cell output (whenever results are discussed)
* [x] I have checked that cell outputs are not incredibly long (this applies also to `DataFrames`)
* [x] Formatting looks correctly on the Sphinx render (bold, italics, figure placing)

# Code review

* Time it took to execute (approx.):
* [ ] Variable and function names follow snake case rules (e.g. `a_variable_name` vs `aVariableName`)
* [ ] Spacing follows PEP8 (run Black on the code cells if needed)
* [ ] Code line are under 99 characters each (run `black -l 99`)
* [ ] Comments are useful and well placed
* [ ] There are no unpythonic idioms like `for i in range(len(list))` (see slides)
* [ ] All 3rd party dependencies are listed at the top of the notebook
* [ ] I have marked all code cell with output referenced in markdown cells with the label `# TODO: CI`
* [ ] I have identified potential candidates for a code refactor / useful functions
* [ ] All `import ...` lines are at the top (practice part) cell, ordered by standard library / 3rd party packages / our own (`teachopencadd.*`)
* [ ] I have update the relative paths to absolute paths.
* List here unfamiliar libraries you find in the imports and their intended use:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d3ec6b0d2d04`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.