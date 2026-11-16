# Issue

**Title:** fix nested-yaml bug

## Description

**Issue Number.** Is this pull request related to any outstanding issues? If so, list the issue number.  


**Describe the changes made.** A clear and concise description of what the problem is and what you did to fix it. E.g. [...] was happening and I've changed [...] to fix it.  
When creating a new nested entry with YAMLConfig, it would wrongly place the new entry at the last existing level. This PR fixes the issue by appropriately descending into the newly created levels.

**Goals and Outstanding Issues.** A clear and concise list of goals (to be) accomplished.  
- [x] Fixed the bug described above.

**Major files changed.**  
- [x] src/westpa/core/yamlcfg.py
- [x] tests/test_yamlfe.py

**Status.**
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] I have read the CONTRIBUTING document.
- [x] My code follows the code style of this project.
- [x] I have added tests to cover my changes.
- [x] All new and existing tests passed.

**Additional context.** Add any other context or screenshots about the pull request here.  

Test case in Python session:
```
from westpa.core.yamlcfg import YAMLConfig

config = YAMLConfig()
config._data = {'west': {'system_options': {'pcoord_ndim': 2}}}
config['west', 'test', 'blah'] = 3

print(config)
try:
   # Expected Output
    assert config['west', 'test', 'blah'] == 2
except KeyError:
   # Faulty Output
    assert config['west', 'system_options', 'test'] == {}
    assert config['west', 'system_options', 'blah'] == 3
    raise ValueError('The faulty outputs are produced.')

```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `080367e9ed7b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.