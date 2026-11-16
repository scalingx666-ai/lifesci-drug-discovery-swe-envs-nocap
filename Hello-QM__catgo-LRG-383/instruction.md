# Issue

**Title:** fix(ci): make Build STT accelerator workflow actually produce binaries

## Description

Fixes the new `Build STT accelerator` workflow so it builds + publishes whisper.cpp Vulkan/Metal binaries (verified green on stt-accel-v1):
- build-whispercpp.sh: resolve OUT to absolute before cd into temp workdir (relative OUT was deleted by the cleanup trap → empty dist).
- Linux runner ubuntu-24.04 (glslc has no apt package on 22.04).
- Windows Vulkan SDK `latest` (pinned 1.3.275.0 404'd on LunarG).
- Windows: clone whisper.cpp into RUNNER_TEMP, not `src` (collides with the repo's own src/).
- manifest job: set GH_REPO (job has no checkout).

Verified: linux-x64-vulkan, macos-arm64-metal, windows-x64-vulkan all green; manifest published; in-app manifest URL returns 200.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7f0ea66d8f01`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.