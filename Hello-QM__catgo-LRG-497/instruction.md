# Issue

**Title:** fix(pip): make the pip-installed catgo wheel actually launch (1.4.5.post1)

## Description

## Bug
\`pip install catgo\` (1.4.5) installs and \`catgo --help\` works, but \`catgo app\` / \`serve\` / \`status\` crash with \`ModuleNotFoundError\`. The wheel installs but the app never launches.

## Root cause
The server imports several **top-level** modules by **bare name** — \`main\`, the full \`workflow\` engine (\`workflow.node_sets\`, \`workflow.engines\`, …), and \`plugin_loader\`. These live *outside* the \`catgo\` package, so \`packages=["catgo"]\` never shipped them in the wheel. They only resolve in a source/editable checkout (where \`server/\` is on \`sys.path\`). There's also a name clash: a *different*, smaller \`catgo.workflow\` exists, so they can't simply be merged.

## Fix
- **Force-include** \`main.py\`, \`workflow/\`, \`plugin_loader.py\`, \`mcp_server.py\` under \`catgo/_bundled/\` in the wheel.
- \`_ensure_sys_path()\` adds \`catgo/_bundled\` to \`sys.path\` (first, so bare \`import workflow\` picks the full engine). In a source checkout that dir doesn't exist → **no-op**, so the editable dev install is untouched.
- Version → **1.4.5.post1** (packaging-only rebuild; PyPI is immutable, so 1.4.5 can't be re-uploaded — a post-release keeps the 1.4.5 identity).

## Verification
Built the wheel and installed it into a **clean venv** (not the dev tree): \`catgo status\` runs cleanly and \`catgo serve\` returns **API 200 / SPA UI 200 / MCP endpoint live**.

Desktop app version is unaffected (stays 1.4.5); this is a pip-package-only fix.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `006a9081f408`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.