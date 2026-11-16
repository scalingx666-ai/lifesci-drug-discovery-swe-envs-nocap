# Issue

**Title:** fix: ai agents4 pharma docker gpu fix

## Description

# For authors
<img width="1780" alt="Screenshot 2025-04-12 at 20 13 25" src="https://github.com/user-attachments/assets/7b63d5f4-fa82-4b16-b62b-d4c769a11e3e" />

##### This screenshot shows the utilisation of my Nvidia GPU(when I tested the application locally -> you can see in the MEM section the model is loaded and it take ~700mb of Vram)

## Description
The previous approach used `docker-compose` profiles and service-specific logic for launching CPU/NVIDIA/AMD variants of the Ollama container. However, this led to maintenance overhead, fragile synchronization, and issues with model readiness across platforms.

This PR introduces a streamlined, production-ready startup system that dynamically adapts to the host's hardware and ensures the Ollama model is fully available before starting the app.

**Key changes:**

- **Introduces a unified `startup.sh` script** that:    
    - Detects GPU type (NVIDIA, AMD, or CPU fallback).        
    - Selects the appropriate `ollama` image (`latest` or `rocm`).        
    - Launches `ollama` via `docker run` for GPU types with correct runtime and entrypoint settings.        
    - Falls back to `docker compose` for CPU.        
    - Waits for the Ollama API and pulls the `nomic-embed-text` model reliably.        
    - Starts `talk2aiagents4pharma` / `talk2knowledgegraphs` only after model availability.
        
- **Replaces multi-profile `docker-compose.yml`** with a unified configuration that works across all hardware without profile switching.
    
- **Simplifies `ollama` service definition**:   
    - Uses a single, minimal entrypoint for CPU (`command: ollama serve`).        
    - Network made external for compatibility with `docker run`.
        
- **Improves startup resilience**:
    
    - Handles network creation.        
    - Replaces reliance on healthchecks with direct API readiness check.
        

**Benefits:**

- One Click On-boarding for users just by using one command: 
```sh
chmod +x startup.sh
./startup.sh
```
- Cross-platform support: NVIDIA, AMD, and CPU work out of the box.  
- Eliminates healthcheck dependency inside Ollama containers.    
- Guarantees application doesn't start until model is fully loaded.
- Easier to maintain, test, and debug.
    

This update makes the setup fully production-ready with clean GPU detection, safe container orchestration, and synchronized model loading. 

## Major Update to the README.md as well for easier on-boarding for the users.   
-> Divided into three sections, thanks to the suggestion by @gurdeep330 
-> In the following order:
1. Docker (stable-release)
2. git (for developers and contributors)
3. pip (beta-release)

Please view the updated README.md using this [link](https://github.com/ansh-info/AIAgents4Pharma/tree/Fix/AIAgents4Pharma-Docker-Gpu-Fix)

## Fixes # (issue) Mention the issue number.
#129 

## Type of change
Please delete options that are not relevant.
- [x] Bug fix (non-breaking change which fixes an issue)
- [x] New feature (non-breaking change which adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to not work as expected)
- [x] This change requires a documentation update

## How Has This Been Tested?
Please describe the tests you conducted to verify your changes. These may involve creating new test scripts or updating existing ones.
- [ ] Added new test(s) in the ```tests``` folder
- [ ] Added new function(s) to an existing test(s) (e.g.: ```tests/testX.py```)
- [x] No new tests added (Please explain the rationale in this case)

## Checklist
- [x] My code follows the style guidelines mentioned in the Code/DevOps guides
- [x] I have commented my code, particularly in hard-to-understand areas
- [x] I have made corresponding changes to the documentation (e.g. MkDocs)
- [x] My changes generate no new warnings
- [x] I have added or updated tests (in the ```tests``` folder) that prove my fix is effective or that my feature works
- [x] New and existing tests pass locally with my changes
- [x] Any dependent changes have been merged and published in downstream modules

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fbf5bfb9f228`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.