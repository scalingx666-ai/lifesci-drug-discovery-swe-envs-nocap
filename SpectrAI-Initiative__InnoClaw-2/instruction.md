# Issue

**Title:** Fix Claude Code setup skill: move to .claude/commands/ and update README

## Description

`claude /setup` fails with "unknown skill" because the skill file lives in `.claude/setup/SKILL.md` instead of Claude Code's expected `.claude/commands/` directory. The file also still references the old project name "VibeLab".

### Changes

- **Move skill file** from `.claude/setup/SKILL.md` → `.claude/commands/setup.md` (standard Claude Code custom commands path)
- **Fix stale references**: "VibeLab" → "InnoClaw", `vibelab.db` → `innoclaw.db`; drop redundant `name` frontmatter field (derived from filename)
- **Update `.gitignore`** allowlist from `.claude/setup/` to `.claude/commands/`
- **Rewrite README Quick Start** with explicit 3-step instructions and a warning about the correct invocation:

```bash
# Step 1: Clone
git clone https://github.com/zjowowen/InnoClaw.git && cd InnoClaw

# Step 2: Enter Claude Code
claude

# Step 3: Inside Claude Code, run:
/project:setup
```

> ⚠️ `claude /setup` directly in terminal → "unknown skill" error. Must enter Claude Code first, then invoke `/project:setup`.

<!-- START COPILOT ORIGINAL PROMPT -->

<details>

<summary>Original prompt</summary>

>
> ----
>
> *This section details on the original issue you should resolve*
>
> <issue_title>Claude Code配置方式的skill出现问题</issue_title>
> <issue_description>### Bug Description
>
> <img width="1118" height="548" alt="Image" src="https://github.com/user-attachments/assets/b2e30b68-f99c-4070-bacf-a651108a9dbc" />
> 采用Claude Code配置出现下面的unknown skill的问题
>
> ![Image](https://github.com/user-attachments/assets/f6e33558-41f3-49dd-991d-cb94bccc7909)
>
> ### Steps to Reproduce
>
> git clone https://github.com/zjowowen/notebooklm.git
> cd notebooklm
> claude /setup
>
> ### Expected Behavior
>
> 正常进行配置
>
> ### Actual Behavior
>
> 报错unknown skill
>
> ### LabClaw Version
>
> date: 26/3/9
>
> ### Node.js Version
>
> 20.x
>
> ### Operating System
>
> Linux
>
> ### Relevant Log Output
>
> ```shell
>
> ```
>
> ### Additional Context
>
> _No response_</issue_description>
>
> <agent_instructions>结合这个issue，请更改readme，写清楚进入Claude code之后如何一步一步用Claude code自动安装</agent_instructions>
>
> ## Comments on the Issue (you are @copilot in this section)
>
> <comments>
> </comments>
>

</details>

<!-- START COPILOT CODING AGENT SUFFIX -->

- Fixes zjowowen/InnoClaw#1

<!-- START COPILOT CODING AGENT TIPS -->
---

💡 You can make Copilot smarter by setting up custom instructions, customizing its development environment and configuring Model Context Protocol (MCP) servers. Learn more [Copilot coding agent tips](https://gh.io/copilot-coding-agent-tips) in the docs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `db20d18fb04c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.