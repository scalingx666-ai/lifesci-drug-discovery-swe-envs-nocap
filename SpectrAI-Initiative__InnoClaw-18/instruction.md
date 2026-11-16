# Issue

**Title:** fix: auto-focus file preview tab on sidebar file selection

## Description

Clicking a file in the sidebar created a new preview tab but didn't focus it — the previously active tab stayed in front.

### Cause

`setActiveTabId` was called inside `setPreviewTabs`'s updater function. React updater functions must be pure; the nested state setter call is a side effect that React can suppress.

### Fix

Introduced a `tabsRef` to read current tabs without stale closures, and moved `setActiveTabId` out of `setPreviewTabs` updaters so both are top-level calls that batch correctly.

```ts
// Before — side effect inside updater, setActiveTabId can be dropped
setPreviewTabs((prev) => {
  const existing = prev.find(…);
  if (existing) {
    setActiveTabId(existing.id); // ← side effect in pure function
    return prev;
  }
  // …
  setActiveTabId(id);
  return [...prev, tab];
});

// After — both setters are independent top-level calls
const current = tabsRef.current;
const existing = current.find(…);
if (existing) {
  setActiveTabId(existing.id);
  return;
}
// …
setPreviewTabs([...current, tab]);
setActiveTabId(id);
```

Applied the same refactor to `openFileTab`, `openArticleTab`, and `closeTab`.

<!-- START COPILOT ORIGINAL PROMPT -->

<details>

<summary>Original prompt</summary>

>
> ----
>
> *This section details on the original issue you should resolve*
>
> <issue_title>File preview tab should auto-focus when selecting a file from the left sidebar</issue_title>
> <issue_description>### Problem Statement
>
>
>
> When I click a file in the left sidebar file list, a new tab for that file is added to the top bar on the right, but the newly opened tab is not brought to the front. As a result, I don’t immediately see the file preview I just clicked.
>
> **Expected behavior**
>
> - When I click a file in the left sidebar:
>   - If there is no existing tab for that file, a new tab should be created **and automatically focused**, so its preview is visible right away.
>   - If there is already an existing tab for that file, that tab should be **brought to the front** (focused), instead of opening a duplicate or leaving another tab active.
>
> **Actual behavior**
>
> - Clicking a file in the left sidebar:
>   - Adds a new tab entry for the file in the top bar on the right, **but does not focus it**.
>   - The previously active tab remains in front, so I have to manually click the newly added tab to see the file preview.
>
> **Why this matters**
>
> - This breaks the usual expectation from IDEs and file explorers (VS Code, editors, etc.), where clicking a file directly shows its contents.
> - It adds an extra click for every file navigation and makes it feel like the click “did nothing” until you notice a new background tab.
>
> **Suggested fix**
>
> - On file selection from the left sidebar:
>   - Find or create the corresponding tab.
>   - Set that tab as the active tab immediately, so the preview switches to the selected file.
>
> ### Proposed Solution
>
> see statement
>
> ### Alternatives Considered
>
> _No response_
>
> ### Feature Area
>
> AI / Chat / Agent
>
> ### Additional Context
>
> _No response_</issue_description>
>
> <agent_instructions>Please refine the code to realize the enhancement.</agent_instructions>
>
> ## Comments on the Issue (you are @copilot in this section)
>
> <comments>
> </comments>
>

</details>

<!-- START COPILOT CODING AGENT SUFFIX -->

- Fixes zjowowen/InnoClaw#16

<!-- START COPILOT CODING AGENT TIPS -->
---

💡 You can make Copilot smarter by setting up custom instructions, customizing its development environment and configuring Model Context Protocol (MCP) servers. Learn more [Copilot coding agent tips](https://gh.io/copilot-coding-agent-tips) in the docs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `65e08f940ac9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.