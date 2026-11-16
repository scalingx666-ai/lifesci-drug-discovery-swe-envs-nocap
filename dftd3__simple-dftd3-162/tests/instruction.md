# Issue

**Title:** Guard type generic macro from C++ compilation

## Description

The `dftd3_delete` type generic macro uses C11's `_Generic`, which is incompatible with C++. Including the header in C++ code fails compilation.

## Changes

- Wrapped `dftd3_delete` macro with `#ifndef __cplusplus` guard in `include/s-dftd3.h`

## Usage

**C code** continues using the type generic macro:
```c
dftd3_error error = dftd3_new_error();
dftd3_delete(error);
```

**C++ code** calls specific delete functions:
```cpp
dftd3_error error = dftd3_new_error();
dftd3_delete_error(&error);  // macro not available in C++
```

<!-- START COPILOT ORIGINAL PROMPT -->

<details>

<summary>Original prompt</summary>

>
> ----
>
> *This section details on the original issue you should resolve*
>
> <issue_title>Type generic macro for C header not working for C++ usage</issue_title>
> <issue_description>The type generic macro for C should not be exposed when using in C++.</issue_description>
>
> <agent_instructions>Do not expose type generic macros if C++ compiler is used.</agent_instructions>
>
> ## Comments on the Issue (you are @copilot in this section)
>
> <comments>
> </comments>
>

</details>

<!-- START COPILOT CODING AGENT SUFFIX -->

- Fixes dftd3/simple-dftd3#159

<!-- START COPILOT CODING AGENT TIPS -->
---

💡 You can make Copilot smarter by setting up custom instructions, customizing its development environment and configuring Model Context Protocol (MCP) servers. Learn more [Copilot coding agent tips](https://gh.io/copilot-coding-agent-tips) in the docs.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `80b548db6583`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.