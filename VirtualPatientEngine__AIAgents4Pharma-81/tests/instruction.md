# Issue

**Title:** feat: Add tool for extracting annotions of species in an ODE model

## Description

# For authors

https://github.com/user-attachments/assets/98cc41fa-9315-4296-8c5c-dbe70c900a3a

## Description

This PR introduces a new tool in Talk2BioModels that helps retrieve species annotations from a model. 
When the tool is prompted **tool uses get_miriam_annotation** function from basico library in the backend  
to retrieve the annotations of the specified species.

When this function is called, it returns the following details:

- Name – The species name as recorded in the database.
- URL – A link to an external database where the species is listed.
- Qualifier – A category or tag that describes the species.

However, the species name is often not very informative, Hence I have developed modules that make API calls to the external databases to fetch the descriptions of the species name. 
Since different species are listed in different databases, fetching their descriptions requires extra steps.

### How the Tool Fetches Descriptions

The species URLs point to multiple external databases, where more detailed descriptions are available. 
I have implemented three API handler files to retrieve description from specific set of databases using the provided URL.

When a user asks for a species annotation, the tool first retrieves the basic details (URL, Name, Qualifier).
Then, based on which database the species belongs to, the tool calls the appropriate API handler file to fetch its description.
Finally, all the information is displayed in an easy-to-read table.

### Results Are Shown to the User is in the demo

The retrieved annotations are displayed in a scrollable table with the following columns:

* Species Name   : The name of the species.
* Description	    : A brief explanation of the species from the database.
* Database	    : The name of the database where the species is listed.
* ID	                    : A unique identifier, shown as a clickable hyperlink that directs the user to the species database page.
* Qualifier	    : Additional information about the species annotation.

### What This Tool Can Do :

✅ Retrieve annotations for one or multiple species in a model.
✅ Fetch all species annotations in a given model.
✅ Remember the model ID from chat history, so users don’t need to enter it each time.
✅ Handle errors gracefully – If a species is not found or its description is missing, the user is notified in the front end.

### Upcoming Feature Enhancements
This version only allows users to view species annotations, but future updates will add more features:

- Adding more Databases for API Calling
    Include Databases like interpro and go
- Editing & Updating Annotations
    Users will be able to edit and update species annotations directly in the table.
- Support for Abstract Questions
    Instead of asking for specific species by name, users will be able to make broader requests, such as:
    "Show me annotations of all the InterLeukins in the model ."

##   (issue)

## Type of change
Please delete options that are not relevant.
- [ ] Bug fix (non-breaking change which fixes an issue)
- [x] New feature (non-breaking change which adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to not work as expected)
- [x] This change requires a documentation update

## How Has This Been Tested?
Please describe the tests you conducted to verify your changes. These may involve creating new test scripts or updating existing ones.
- [x] Added new test ( test_get_annotaion ) in the ```tests``` folder
- [ ] Added new function(s) to an existing test(s) (e.g.: ```tests/testX.py```)
- [ ] No new tests added (Please explain the rationale in this case)

## Checklist
- [x] My code follows the style guidelines mentioned in the Code/DevOps guides
- [x] I have commented my code, particularly in hard-to-understand areas
- [ ] I have made corresponding changes to the documentation (e.g. MkDocs)
- [ ] My changes generate no new warnings
- [x] I have added or updated tests (in the ```tests``` folder) that prove my fix is effective or that my feature works
- [x] New and existing tests pass locally with my changes
- [ ] Any dependent changes have been merged and published in downstream modules

# For reviewers

## Checklist pre-approval
- [ ] Is there enough documentation?  
- [ ] If a new feature has been added, or a bug fixed, has a test been added to confirm good behavior?
- [ ] Does the test(s) successfully test edge/corner cases?
- [ ] Does the PR pass the tests? (if the repository has continuous integration)

## Checklist post-approval
- [ ] Does this PR merge ```develop``` into ```main```? If so, please make sure to add a prefix (feat/fix/chore) and/or a suffix BREAKING CHANGE (if it's a major release) to your commit message.
- [ ] Does this PR close an issue? If so, please make sure to descriptively close this issue when the PR is merged.

## Checklist post-merge
- [ ] When you approve of the PR, merge and close it (Read this [article](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/configuring-pull-request-merges/about-merge-methods-on-github) to know about different merge methods on GitHub)
- [ ] Did this PR merge ```develop``` into ```main``` and is it suppose to run an automated release workflow (if applicable)? If so, please make sure to check under the "Actions" tab to see if the workflow has been initiated, and return later to verify that it has completed successfully.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d64879733ab2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.