# Issue

**Title:** fix(chat): adaptive agent-bridge port + lab link only on landing

## Description

Two independent fixes found while testing CatBot in the Tauri desktop app.

## 1. Adaptive agent-bridge port (fixes CatBot on shared boxes / shipped installs)
The shell decided "agent already running, skip" from a bare TCP connect to :8001 and always pointed the webview there. ANY process holding :8001 (another user, or a random app on a Windows install) → real agent never starts → CatBot `Agent stream failed: Not Found`.

- `/health` gains a `service: "catgo-agent"` identity marker.
- Shell probes `/health` (not just TCP); reuses :8001 only when the marker is present.
- If :8001 is taken by a non-agent, spawn the agent on the next free port.
- Inject `window.__CATGO_AGENT_PORT__` only when an agent is reachable; else the FE uses the relative `/api/agent/*` URL (dev vite plugin). Dev unchanged.

Verified live: with another user squatting :8001, the shell logs "port 8001 is taken … picking a free port" and CatBot connects.

## 2. Lab link only on the landing page
The "Dr. Wanlu Li @UCSD" `position:fixed` badge bled into the workbench. Moved into the landing-page block next to "Star on GitHub" (same visibility) and restyled to match `.github-star` (absolute pill, top-left).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b45b898bd036`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.