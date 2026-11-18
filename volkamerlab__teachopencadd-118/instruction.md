# Issue

**Title:** T027 Kinase similarity: ligand-profile

## Description

## Description

* Talktorial ID: T027
* Title: Kinase similarity: ligand-profile
* Original authors: @t-kimber 
* Reviewer(s): @dominiquesydow, @AndreaVolkamer 
* Date of review:

https://app.reviewnb.com/volkamerlab/teachopencadd/pull/118

## Todos

### Content

- [x] Theory
  - [x] Kinase dataset
  - [x] Kinase similarity descriptor: XXX
- [x] Practical
  - [x] Retrieve and preprocess data
  - [x] Show kinase coverage
  - [x] Compare kinases
  - [x] Visualize similarity as kinase matrix
  - [x] Visualize similarity as phylogenetic tree

### Content review

* Potential labels or categories (e.g. machine learning, small molecules, online APIs): XXXXXXXX
* One line summary: XXXXXXXXXX
* [x] The table of contents reflects the talktorial story-line; order of #, ##, ### headers is correct
* [x] URLs are linked with meaningful words, instead of pasting the URL directly or linking words like `here`.
* [x] I have spell-checked the notebook
* [x] Images have enough resolution to be rendered with quality, without being _too_ heavy.
* [x] All figures have a description
* [ ] Markdown cell content is still in-line with code cell output (whenever results are discussed)
* [ ] I have checked that cell outputs are not incredibly long (this applies also to `DataFrames`)
* [ ] Formatting looks correctly on the Sphinx render (bold, italics, figure placing)

### Code review

* Time it took to execute (approx.):
* [x] Variable and function names follow snake case rules (e.g. `a_variable_name` vs `aVariableName`)
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

## Questions
- [ ] TBA

## Status
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `93f526c7baf5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.