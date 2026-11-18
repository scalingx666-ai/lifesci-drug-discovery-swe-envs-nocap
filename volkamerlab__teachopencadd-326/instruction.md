# Issue

**Title:** [DL Edition] T037: E(3)-invariant graph neural networks

## Description

## Details

* Talktorial ID: 037
* Title: [DL Edition] T037: E(3)-invariant graph neural networks
* Original authors: Joschka Groß
* Reviewer(s): XXX
* Date of review: DD-MM-YYYY

## Content

* One line summary: Introduction to E(3) In-/Equivariant Graph Neural Networks
* Potential labels or categories (e.g. machine learning, small molecules, online APIs): Machine learning, small molecules, graph neural networks, point clouds, 3D information
* Time it took to execute (approx.): 
* [x] I have used the [talktorial template](https://github.com/volkamerlab/teachopencadd/blob/master/teachopencadd/talktorials/T000_template/talktorial.ipynb) and followed the content and formatting suggestions there
* [ ] _Packages_ must be open-sourced and should be installable from `conda-forge`. If you are adding new packages to the TeachOpenCADD environment, please check if already installed packages can perform the same functionality and if not leave a sentence explaining why the new addition is needed. If the new package is not on `conda-forge`, please list them and their intended usage here.
  * `numpy`, `matplotlib`: Already in TeachOpenCADD
  * `pytorch 1.12.1`, `pytorch-cluster 1.6.0`, `pytorch-scatter 2.1.0`, `pytorch-sparse 0.6.15`, `pyg 2.2.0` (conda-forge): pyg (torch_geometric) includes graph neural network and the QM9 dataset we use for the practical part, everzthing else is a dependency of `torch_geometric`, however we also use `pytorch-scatter` explicitly in our EGNN implementation
* [x] _Data_ must be publicly available, preferably accessible via a webserver or downloadable via a URL. Please list the data resources that you use and how to access them:
  * QM9 dataset: Access via ([torch-geometric](https://pytorch-geometric.readthedocs.io/en/latest/modules/datasets.html#torch_geometric.datasets.QM9))

## Content style

* [x] Talktorial includes cross-references to other talktorials if applicable
* [x] The table of contents reflects the talktorial story-line; order of #, ##, ### headers is correct
* [x] URLs are linked with meaningful words, instead of pasting the URL directly or linking words like `here`.
* [x] I have spell-checked the notebook
* [x] Images have enough resolution to be rendered with quality, without being _too_ heavy.
* [x] All figures have a description
* [x] Markdown cell content is still in-line with code cell output (whenever results are discussed)
* [x] I have checked that cell outputs are not incredibly long (this applies also to `DataFrames`) - is 100 lines okay?
* [ ] Formatting looks correctly on the Sphinx render (bold, italics, figure placing)

## Code style

* [x] Variable and function names follow snake case rules (e.g. `a_variable_name` vs `aVariableName`)
* [x] Spacing follows PEP8 (run Black on the code cells if needed)
* [x] Code line are under 99 characters each (run `black-nb -l 99`)
* [x] Comments are useful and well placed
* [x] There are no unpythonic idioms like `for i in range(len(list))` (see slides)
* [x] All 3rd party dependencies are listed at the top of the notebook
* [x] I have marked all code cell with output referenced in markdown cells with the label `# NBVAL_CHECK_OUTPUT`
* [ ] I have identified potential candidates for a code refactor / useful functions
* [x] All `import ...` lines are at the top (practice part) cell, ordered by standard library / 3rd party packages / our own (`teachopencadd.*`)
* [x] I have used absolute paths instead of relative paths
  ```python
  HERE = Path(_dh[-1])
  DATA = HERE / "data"
  ```

## Website
We present our talktorials on our TeachOpenCADD website (https://projects.volkamerlab.org/teachopencadd/), so we have to check as well if the Jupyter notebook renders nicely there.

* [ ] If this PR adds a new talktorial, please follow these steps:
  * [ ] Add your talktorial to the complete list of talktorials [here](https://github.com/volkamerlab/teachopencadd/blob/master/docs/all_talktorials.rst) (at the end).
  * [ ] Add your talktorial to one or multiple of the collections [here](https://github.com/volkamerlab/teachopencadd/blob/master/docs/talktorials.rst). Or propose a new collection section in your PR.
  * [ ] Add your talktorial's `nblink` file by running `python generate_nblinks.py` from within the directory `teachopencadd/docs/talktorials`.
  * [ ] Please complile the website following the instructions [here](https://github.com/volkamerlab/teachopencadd/tree/master/docs).
* [ ] Check the rendering of the talktorial of this PR.
* [ ] Is your talktorial listed [in the talktorial list](https://projects.volkamerlab.org/teachopencadd/all_talktorials.html)?
* [ ] Is your talktorial listed [in the talktorial collections](https://projects.volkamerlab.org/teachopencadd/talktorials.html)?
  * [ ] Add a picture for your talktorial in the collection view by following [these instructions](https://github.com/volkamerlab/teachopencadd/discussions/185). 


## Status
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `728221261f89`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.