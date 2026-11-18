# Issue

**Title:** Add `teachopencadd start workspace` CLI

## Description

## Description
Add `teachopencadd start workspace` CLI that copies talktorials from their location in the `teachopencadd` package to a user-defined folder (**workspace**).

## CLI Behavior
`teachopencadd start .` will copy the [full talktorial folder content](https://github.com/volkamerlab/teachopencadd/tree/master/teachopencadd/talktorials) to a folder called `teachopencadd-talktorials`, which lives in the user-defined workspace (here: working directory `.`)

### Workspace exists and does not contain a `teachopencadd-talktorials` folder, yet
Copy files, list talktorials, give JLab instructions.

```
$ teachopencadd start ~/workspaces

 ___                _               _       _   _  
  |  _   _.  _ |_  / \ ._   _  ._  /   /\  | \ | \ 
  | (/_ (_| (_ | | \_/ |_) (/_ | | \_ /--\ |_/ |_/ 
                       |                           

    version v1.3.0+705.g394f25c
    by @volkamerlab
    

Talktorials available in your workspace:

  - T000_template
  - T001_query_chembl
  - T002_compound_adme
  - T003_compound_unwanted_substructures
  - T004_compound_similarity
  - T005_compound_clustering
  - T006_compound_maximum_common_substructures
  - T007_compound_activity_machine_learning
  - T008_query_pdb
  - T009_compound_ensemble_pharmacophores
  - T010_binding_site_comparison
  - T011_query_online_api_webservices
  - T012_query_klifs
  - T013_query_pubchem
  - T014_binding_site_detection
  - T015_protein_ligand_docking
  - T016_protein_ligand_interactions
  - T017_advanced_nglview_usage
  - T019_md_simulation
  - T020_md_analysis
  - T021_one_hot_encoding
  - T022_ligand_based_screening_neural_network

To start working with the talktorials in JupyterLab run:

    jupyter lab /home/dominique/workspaces/teachopencadd-talktorials

Enjoy!
```

### Workspace exists but contains already a `teachopencadd-talktorials` folder
Inform user that folder already exists, do not overwrite folder, list talktorials, give JLab instructions.

```
$ teachopencadd start ~/workspaces

 ___                _               _       _   _  
  |  _   _.  _ |_  / \ ._   _  ._  /   /\  | \ | \ 
  | (/_ (_| (_ | | \_/ |_) (/_ | | \_ /--\ |_/ |_/ 
                       |                           

    version v1.3.0+703.gc3a6308.dirty
    by @volkamerlab
    
Workspace exists already at location /home/dominique/workspaces/teachopencadd-talktorials.

Talktorials available in your workspace:

  - T000_template
  - T001_query_chembl
  - T002_compound_adme
  - T003_compound_unwanted_substructures
  - T004_compound_similarity
  - T005_compound_clustering
  - T006_compound_maximum_common_substructures
  - T007_compound_activity_machine_learning
  - T008_query_pdb
  - T009_compound_ensemble_pharmacophores
  - T010_binding_site_comparison
  - T011_query_online_api_webservices
  - T012_query_klifs
  - T013_query_pubchem
  - T014_binding_site_detection
  - T015_protein_ligand_docking
  - T016_protein_ligand_interactions
  - T017_advanced_nglview_usage
  - T019_md_simulation
  - T020_md_analysis
  - T021_one_hot_encoding
  - T022_ligand_based_screening_neural_network

To start working with the talktorials in JupyterLab run:

    jupyter lab /home/dominique/workspaces/teachopencadd-talktorials

Enjoy!
```

### Workspace does not exist
Inform user about invalid workspace location, do nothing more.

```
$ teachopencadd start ~/xxx

 ___                _               _       _   _  
  |  _   _.  _ |_  / \ ._   _  ._  /   /\  | \ | \ 
  | (/_ (_| (_ | | \_/ |_) (/_ | | \_ /--\ |_/ |_/ 
                       |                           

    version v1.3.0+705.g394f25c
    by @volkamerlab
    
Could not find user-defined location `/home/dominique/xxx`
```

## Todos
- [x] Implement behavior as shown above
- [x] Implement tests (test exit code, stdout, stderr, number of copied files)
  - [x] Workspace exists, talktorials not there yet 
  - [x] Workspace exists, talktorials already there
  - [x] Workspace does not exist
  - [x] Test JupyterLab command as well?
- [x] Add `pytest-cov` to report code coverage (do not enable CodeCov since most testing is done via `nbval`)

## Question
- [x] Should be remove the Traceback from the last case? Using only `print` instead of `raise` in combo with `sys.exit`?
- [x] Use `logging` instead of `print` - or print ok here?

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c3a6308a706f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.