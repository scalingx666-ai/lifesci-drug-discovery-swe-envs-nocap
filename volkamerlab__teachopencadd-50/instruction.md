# Issue

**Title:** Review T005

## Description

<!-- Talktorial review template -->
<!-- Thank you very much for helping us improve TeachOpenCADD! -->

# Details

* Talktorial ID: 005
* Title: Compound clustering
* Original authors: Calvinna Caswara, Gizem Spriewald
* Reviewer(s): Jaime Rodríguez-Guerra, Dominique Sydow
* Date of review: 2020.09.08

# Content review

* Potential labels or categories (e.g. machine learning, small molecules, online APIs): small molecules, cheminformatics, clustering
* One line summary: _Compound clustering in pharmaceutical research is often based on chemical or structural similarity between compounds to find groups that share properties as well as to design a diverse and representative set for further analysis._
* [X] The table of contents reflects the talktorial story-line; order of #, ##, ### headers is correct
* [X] URLs are linked with meaningful words, instead of pasting the URL directly or linking words like `here`.
* [X] I have spell-checked the notebook
* [X] Images have enough resolution to be rendered with quality, without being _too_ heavy.
* [X] All figures have a description
* [x] Markdown cell content is still in-line with code cell output (whenever results are discussed)
* [X] I have checked that cell outputs are not incredibly long (this applies also to `DataFrames`)
* [X] Formatting looks correctly on the Sphinx render (bold, italics, figure placing)

# Code review

* Time it took to execute (approx.): <3mins
* [X] Variable and function names follow snake case rules (e.g. `a_variable_name` vs `aVariableName`)
* [X] Spacing follows PEP8 (run Black on the code cells if needed)
* [X] Code line are under 99 characters each (run `black -l 99`)
* [X] Comments are useful and well placed
* [X] There are no unpythonic idioms like `for i in range(len(list))` (see slides)
* [X] All 3rd party dependencies are listed at the top of the notebook
* [X] I have marked all code cell with output referenced in markdown cells with the label `# TODO: CI`
* [ ] I have identified potential candidates for a code refactor / useful functions
* [X] All `import ...` lines are at the top (practice part) cell, ordered by standard library / 3rd party packages / our own (`teachopencadd.*`)
* [X] I have update the relative paths to absolute paths.
* List here unfamiliar libraries you find in the imports and their intended use:

# Other issues

* [x] `stringer` ?
* [x] Make sure output is deterministic!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `59b146a63d82`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.