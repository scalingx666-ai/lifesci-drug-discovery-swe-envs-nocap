# Issue

**Title:** Solve diversity_filter issue (diversity_filter not applied even though present in the config file) by changing “if "type" in config:” into “if memory_type:”

## Description

Hello REINVENT team! Thanks a lot for the wonderful tool you created! We noticed a problem using the software and we believe the solution is the following. Please don’t hesitate to come back to us if you think the problem might lie elsewhere 😊 

While using REINVENT version 4.4 to generate molecules with the staged_learning mode, and with a diversity_filter in the .toml configuration file, as follows:  
 
![image](https://github.com/user-attachments/assets/34264e96-a88c-4dd8-a27e-6856e0f7bad2)

a lack of molecular variety in the generated molecules was observed.  

An analysis of the .log file showed that the line “Using diversity_filter {memory_type}” was missing (even though the diversity filter section is present in the configuration file as shown above). This line should be printed in the setup_diversity_filter function present in REINVENT4 --> reinvent --> runmodes --> RL --> run_staged_learning.py, thus suggesting an issue in this function. 

By adding information in the log file via logger.info() lines, it has been shown that the memory_type is retrieved from the configuration as expected. However, the “if ‘type’ in config:” loop is not entered. In this case, the config is "type='IdenticalMurckoScaffold' bucket_size=25 minscore=0.4 minsimilarity=0.4 penalty_multiplier=0.5", displaying a “type” element. However, the type of config is not < str>, but <class 'reinvent.runmodes.RL.validation.SectionDiversityFilter'>, which may explain why “type” is not found in “config”. In addition, a comparison between previous versions of REINVENT and the actual version showed that the type of “config” has been changed (from < dict> to < class>), but this test has not been modified. 

Testing “if memory_type:” instead of “if ‘type’ in config:” solved the issue (diversity_filter used when present in the config file, and not used if not present in the config file). 

_Additional note:_ it can also be noted that if no “type” is provided in the “diversity_filter” section, the following error occur when launching the reinvent command in the terminal: 

"Field required [type=missing, input_value={'bucket_size': 25, 'minscore': 0.4}, input_type=dict]"

thus questioning the usefulness of the test in this version of REINVENT.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e2befbfeba2b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.