# Issue

**Title:** T012 - Data acquisition from KLIFS

## Description

<!-- Talktorial review template -->
<!-- Thank you very much for helping us improve TeachOpenCADD! -->

# Details

* Talktorial ID: T012
* Title: Data acquisition from KLIFS
* Original authors: @jaimergp, @dominiquesydow 
* Reviewer(s): @dominiquesydow, @schallerdavid 
* Date of review: 2020-12-02

# Content review

* Potential labels or categories (e.g. machine learning, small molecules, online APIs): __kinases, online APIs, protein-ligand complex, EGFR, profiling data, off-targets__
* One line summary: __Structures and bound ligands for a query kinase are fetched from KLIFS using the website's Swagger API.__
* [x] The table of contents reflects the talktorial story-line; order of #, ##, ### headers is correct
* [x] URLs are linked with meaningful words, instead of pasting the URL directly or linking words like `here`.
* [x] I have spell-checked the notebook
* [x] Images have enough resolution to be rendered with quality, without being _too_ heavy.
* [x] All figures have a description
* [x] Markdown cell content is still in-line with code cell output (whenever results are discussed)
* [x] I have checked that cell outputs are not incredibly long (this applies also to `DataFrames`)
* [x] Formatting looks correctly on the Sphinx render (bold, italics, figure placing)

# Code review

* Time it took to execute (approx.): 20 s
* [x] Variable and function names follow snake case rules (e.g. `a_variable_name` vs `aVariableName`)
* [x] Spacing follows PEP8 (run Black on the code cells if needed)
* [x] Code line are under 99 characters each (run `black -l 99`)
* [x] Comments are useful and well placed
* [x] There are no unpythonic idioms like `for i in range(len(list))` (see slides)
* [x] All 3rd party dependencies are listed at the top of the notebook
* [x] I have marked all code cell with output referenced in markdown cells with the label `# TODO: CI` - added `# NBVAL_CHECK_OUTPUT`
* [x] I have identified potential candidates for a code refactor / useful functions: KLIFS queries are already part of `opencadd`
* [x] All `import ...` lines are at the top (practice part) cell, ordered by standard library / 3rd party packages / our own (`teachopencadd.*`)
* [x] I have update the relative paths to absolute paths: Not needed in this stand-alone online API talkorial
* List here unfamiliar libraries you find in the imports and their intended use: All libraries known and checked!

# TODOs

* [x] Update environment: Use latest `opencadd` version
* [x] Update `opencadd.databases.klifs` TODO after  is merged!
* [x] Reread the full talktorial one more time to check again for typos
* [x] Prepare talktorial TOC
* [x] Replace wiki reference with EGFR and Gefitinib references
* [x] Add discussion

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3f2208d936b6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.