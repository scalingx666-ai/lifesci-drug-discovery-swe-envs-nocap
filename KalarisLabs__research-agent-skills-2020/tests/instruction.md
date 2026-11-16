# Issue

**Title:** ci: bump step-security/harden-runner from 2.22.3 to 2.22.4 in the actions group

## Description

Bumps the actions group with 1 update: [step-security/harden-runner](https://github.com/step-security/harden-runner).

Updates `step-security/harden-runner` from 2.22.3 to 2.22.4
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/step-security/harden-runner/releases">step-security/harden-runner's releases</a>.</em></p>
<blockquote>
<h2>v2.22.4</h2>
<h2>What's Changed</h2>
<ul>
<li>Fixed a Linux agent memory leak that could cause runners to run out of memory during jobs with heavy process or network activity.</li>
<li>The workaround for GitHub’s DNS resolver and outbound proxy experiment on GitHub-hosted Linux runners now defaults to enabled when feature flags can’t be fetched.</li>
<li>Improved HTTP/2 TLS interception on Linux (enterprise tier).</li>
<li>Added retries for failed monitoring API requests, improving reliability of monitoring initialization and raw-event uploads.</li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/step-security/harden-runner/compare/v2.22.3...v2.22.4">https://github.com/step-security/harden-runner/compare/v2.22.3...v2.22.4</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>1d88384</code></a> Merge pull request <a href="">#716</a> from step-security/rc-48</li>
<li><a href=""><code>26249c0</code></a> Merge pull request <a href="">#712</a> from Prateek-stepsecurity/pn/monitor-retry</li>
<li><a href=""><code>b5a70cf</code></a> Treat 409 from /monitor as terminal and add retry tests</li>
<li><a href=""><code>0a48cce</code></a> Retry /monitor call up to 3 times on failure</li>
<li><a href=""><code>967c33e</code></a> Merge pull request <a href="">#715</a> from step-security/rc-47</li>
<li><a href=""><code>4fa77e8</code></a> Merge pull request <a href="">#714</a> from h0x0er/jatin/agent-v1.9.6-v0.18.1</li>
<li><a href=""><code>dd2b975</code></a> bump agent versions</li>
<li>See full diff in <a href="https://github.com/step-security/harden-runner/compare/46b06cea07f9e64621fdf066ba77ac6915163d43...1d88384fd173af6ecb012dfd0264a306b711241a">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=step-security/harden-runner&package-manager=github_actions&previous-version=2.22.3&new-version=2.22.4)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

Dependabot will resolve any conflicts with this PR as long as you don't alter it yourself. You can also trigger a rebase manually by commenting `@dependabot rebase`.

[//]: # (dependabot-automerge-start)
[//]: # (dependabot-automerge-end)

---

<details>
<summary>Dependabot commands and options</summary>
<br />

You can trigger Dependabot actions by commenting on this PR:
- `@dependabot rebase` will rebase this PR
- `@dependabot recreate` will recreate this PR, overwriting any edits that have been made to it
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore <dependency name> major version` will close this group update PR and stop Dependabot creating any more for the specific dependency's major version (unless you unignore this specific dependency's major version or upgrade to it yourself)
- `@dependabot ignore <dependency name> minor version` will close this group update PR and stop Dependabot creating any more for the specific dependency's minor version (unless you unignore this specific dependency's minor version or upgrade to it yourself)
- `@dependabot ignore <dependency name>` will close this group update PR and stop Dependabot creating any more for the specific dependency (unless you unignore this specific dependency or upgrade to it yourself)
- `@dependabot unignore <dependency name>` will remove all of the ignore conditions of the specified dependency
- `@dependabot unignore <dependency name> <ignore condition>` will remove the ignore condition of the specified dependency and ignore conditions

</details>

<!-- codesmith:footer -->
---
<a href="https://backend.blacksmith.sh/track/enable-autofix?expires=1797090386&installation_model_id=444357&pr_number=2020&ref=codesmith_pr_footer&repository=KalarisLabs%2Fresearch-agent-skills&return_to=https%3A%2F%2Fgithub.com%2FKalarisLabs%2Fresearch-agent-skills%2Fpull%2F2020&signature=db0de91e5dda1f4336c1ed960d163725b41582aeee85608ec66489ecf6f3a2f2"><picture><source media="(prefers-color-scheme: dark)" srcset="https://pr-comments-assets.blacksmith.sh/codesmith/autofix-with-codesmith-dark.svg"><source media="(prefers-color-scheme: light)" srcset="https://pr-comments-assets.blacksmith.sh/codesmith/autofix-with-codesmith-light.svg"><img alt="Autofix with [code]smith" src="https://pr-comments-assets.blacksmith.sh/codesmith/autofix-with-codesmith-dark-3x.png" width="190" height="28"></picture></a>
<sup><a href="https://app.blacksmith.sh/KalarisLabs/codesmith/research-agent-skills/pr/2020?autoLogin=true&ref=codesmith_pr_footer">Open in [code]smith</a> · Need help on this PR? Tag <code>@codesmith-bot</code> with what you need.</sup>

<!-- codesmith:autofix:disabled -->
<!-- /codesmith:footer -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d98cda600723`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.