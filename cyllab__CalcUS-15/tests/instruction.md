# Issue

**Title:** GSoC Final Submission - Merging Calcus 2.0 with the flowchart version of CalcUS

## Description

**Pull Request for the final submission of the GSoC’22 Project with CalcUS (Open Chemistry)**

**About CalcUS**

CalcUS aims to democratize access to computational chemistry by providing a user-friendly web interface to simplify running and analyzing quantum mechanical calculations. These calculations allow the researchers to understand better the properties of molecules or the underlying mechanisms of chemical reactions. Multiple distinct calculations have to be performed to calculate the molecular geometry, energy, possible vibrations and optical properties, etc, of the molecules. But, Quantum chemistry projects often involve the same series of sequential calculations. Currently, each calculation has to be launched manually, which is often not necessary. This project aims to add the feature to create custom multi-step calculation protocols as well as the underlying mechanics which make the protocols run smoothly.

**About my project**

My project aimed to implement a multi-step calculation protocol to create the data structures to store these protocols and their progress, integrate the automated launch of subsequent steps using the current calculation handling code, add simple verifications after each step completion, and write relevant unit and/or integration tests.
This project aimed to add a way to chain multiple calculations with different parameters. It will enable interfaces with flowchart-like processes. 

![image](https://user-images.githubusercontent.com/65958420/200138878-81f5fc0e-51cc-4d8c-8a4e-22543ccf1b93.png)


The user creates the above workflow in some web plugin and can then be used on multiple input files at wish. CalcUS will generate two calculations per input, execute them, and will perform additional calculations on them. The motivation to add this is to save time for the user and automatically queue the next steps he would do anyway before analysis. It can also reduce mistakes by automatically tracking the progress of each input and applying the exact same parameters to all inputs. 

**Some important links**

CalcUS GitHub - https://github.com/cyllab/CalcUS
My GitHub - https://github.com/div-yam
CalcUS Installation Guide - https://calcus.readthedocs.io/en/latest/installation.html

My mentor - [Raphaël Robidas](https://github.com/RaphaelRobidas)

**This pull request contains all the progress during my contribution period in Google Summer of Code. All my commits got squashed into this single , due to re-reverting my changes. All my original commits can be seen in this branch [FlowchartxCalcus2.0](https://github.com/div-yam/CalcUS/tree/FlowchartxCalcus2.0).** 

**Goals**

- Modify the frontend part to create the flowcharts as easily as possible.
- Modify some pages to indicate the workflow linked to each result.
- Create new database models to save and load these flowcharts.
- Write and modify code to handle the calculation creation and execution.
- Automatic detection of incorrect calculation termination or crash, and either handling it automatically or asking the user to choose an action to take.
- Write code to launch the next steps of the workflow when a calculation finishes successfully.
- Write unit and integration tests to make sure this feature keeps working. The integration tests will use the Selenium WebDriver.


**Work done in the PR**

- Created the web interface for creating flowcharts, using Flowy library, and modifying the library to make it suitable for CalcUS and our purpose. After trying many libraries, we finalised that [Flowy](https://github.com/alyssaxuu/flowy) would be best suited for the purpose as it was open-source, MIT licensed, we could export the flowcharts as a JSON file, and it was not difficult to implement. 
- Created the “Flowchart” model to save the flowchart into the database.
- Made arrangements for saving the flowchart thus created in JSON format to the database, along with all the necessary data sets.
- Wrote code for retrieving those flowcharts saved in the database.
- Integrated the parameters formed with each node of the flowchart and made sure that the flowcharts and parameters were linked to each other and could be properly retrieved in the frontend as well. 
- Took the common input for the calculations (molecule structure, name etc.) and made sure the submitted input was getting submitted without any errors.
- Linked the submitted input with all the calculations of a given flowchart. 
- The next step was linking the output of one calculation to the input of the next input, that is, implementing the multiple calculations to launch simultaneously. 
- Made sure that the generated output was correct and threw errors in case of any ambiguity. 
- Wrote some tests to ensure that the code ran and passed all real-life scenarios. 
- Integrated the code with the cloud version of CalcUS (CalcUS 2.0), which require some critical changes to be made in the code. 

**Additional improvements that could be made to the code**

- Improving the workflow of the calculation submission. 
- Automatic detection and handling of calculation crashes.
- Visualization of results on the web interface. 
- Creating all the global variables used in one place in flowchart.html. 
- Writing some more tests for the code written recently.
- Improving the front end of the “flowchart” page.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b2c81f10f24a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.