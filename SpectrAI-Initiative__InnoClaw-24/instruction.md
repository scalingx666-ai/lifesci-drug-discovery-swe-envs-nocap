# Issue

**Title:** Enhance Skill Import: Local Folder Batch Import & Claude Code Integration

## Description

Skill import was limited to single `.md` files or GitHub URLs. This adds folder-level batch import and automatic discovery from local Claude Code configuration.

## New: Local Folder Import (`webkitdirectory`)
- New **Folder** tab in the import dialog uses `webkitdirectory` for folder selection
- Client-side pattern matching filters to importable files: `*/skills/*/SKILL.md`, `*/commands/*.md`, `*/agents/*.md` (excluding `skills/*/agents/`)
- Progress bar tracks `current / total` files during batch import

## New: Claude Code Integration
- New **Claude Code** tab scans `~/.claude/commands/*.md` and `~/.claude/skills/*/SKILL.md` via a server-side API call
- Accepts an optional custom path (defaults to `~/.claude`; `~` is resolved via `os.homedir()`)
- New endpoints: `POST /api/skills/claude-import` (import) and `GET /api/skills/claude-import` (preview/discover)

## Refactor: Shared Insert Utility
- `insertSkill` and `parseSkillMd` extracted from `import/route.ts` into `src/lib/db/skills-insert.ts` to be shared between both import routes, eliminating ~80 lines of duplication

## i18n
- 9 new keys added to both `en.json` and `zh.json` for all new UI surfaces

<!-- START COPILOT ORIGINAL PROMPT -->

<details>

<summary>Original prompt</summary>

>
> ----
>
> *This section details on the original issue you should resolve*
>
> <issue_title>Enhance Skill Import: Support Local Folder Import & Claude Code Skills Integration</issue_title>
> <issue_description>### Problem Statement
>
> 当前技能导入功能仅支持：
>   - 从 GitHub 仓库 URL 导入（单个 SKILL.md 或批量发现）
>   - 从本地文件导入单个 .md 文件
>
>
>
> ### Proposed Solution
>
>   建议增加：
>   1. 本地文件夹批量导入 - 支持选择本地文件夹，自动发现并导入多个技能
>   2. Claude Code 技能集成 - 自动读取本地 Claude Code 已配置的技能目录
>
> ### Alternatives Considered
>
> _No response_
>
> ### Feature Area
>
> Skills System
>
> ### Additional Context
>
> Detailed Description:
>
>   1. 本地文件夹批量导入
>   当前限制 (src/components/skills/skill-import-dialog.tsx:177-196)
>   - 仅支持单文件选择 (<input type="file" accept=".md">)
>   - 用户需逐个上传 SKILL.md 文件
>
>   期望功能
>   - 支持文件夹选择 (webkitdirectory 属性)
>   - 自动递归扫描以下文件模式：
>     - */skills/*/SKILL.md
>     - */commands/*.md
>     - */agents/*.md (排除 skills/*/agents/)
>   - 批量导入时显示进度条和导入结果
>
>   2. Claude Code 技能集成
>
>   背景
>   Claude Code 将自定义技能存放在：
>   - ~/.claude/commands/<command-name>.md
>   - ~/.claude/skills/<skill-name>/SKILL.md
>
>   期望功能
>   - 在 Settings 或 Skills 页面增加 "Import from Claude Code" 按钮
>   - 自动扫描默认路径：
>     - macOS: ~/.claude
>     - Linux: ~/.claude
>     - Windows: %USERPROFILE%\.claude
>   - 支持自定义 Claude Code 配置路径</issue_description>
>
> <agent_instructions>Select the most powerful model to consider this issue, solve it and create a PR </agent_instructions>
>
> ## Comments on the Issue (you are @copilot in this section)
>
> <comments>
> </comments>
>

</details>

<!-- START COPILOT CODING AGENT SUFFIX -->

- Fixes zjowowen/InnoClaw#23

<!-- START COPILOT CODING AGENT TIPS -->
---

🔒 GitHub Advanced Security automatically protects Copilot coding agent pull requests. You can protect all pull requests by enabling Advanced Security for your repositories. [Learn more about Advanced Security.](https://gh.io/cca-advanced-security)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eaf31cc73073`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.