# Issue

**Title:** ci(deps): bump SonarSource/sonarqube-scan-action from 5.3.1 to 6.0.0

## Description

Bumps [SonarSource/sonarqube-scan-action](https://github.com/sonarsource/sonarqube-scan-action) from 5.3.1 to 6.0.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/sonarsource/sonarqube-scan-action/releases">SonarSource/sonarqube-scan-action's releases</a>.</em></p>
<blockquote>
<h2>v6.0.0</h2>
<h2>BREAKING CHANGE!</h2>
<p>In order to prevent command-line injection, the actions has been rewritten from Bash to JS, and the <code>args</code> input is now parsed differently. When updating to v6, you might have to update your workflow to change how arguments are quoted.
For example, if you were previously passing:</p>
<pre lang="yaml"><code>- uses: SonarSource/sonarqube-scan-action@&lt;action version&gt;
  with:
    args: &gt;
      -Dsonar.projectName=&quot;My Project&quot;
</code></pre>
<p>you should now pass:</p>
<pre lang="yaml"><code>- uses: SonarSource/sonarqube-scan-action@&lt;action version&gt;
  with:
    args: &gt;
      &quot;-Dsonar.projectName=My Project&quot;
</code></pre>
<p>For more <code>args</code> passing examples, please refer to the <a href="https://github.com/SonarSource/sonarqube-scan-action/tree/master?tab=readme-ov-file#args">README</a> file</p>
<h2>What's Changed</h2>
<ul>
<li>SQSCANGHA-106 Migrate from Bash to JS by <a href="https://github.com/jeremy-davis-sonarsource"><code>@​jeremy-davis-sonarsource</code></a> in <a href="">SonarSource/sonarqube-scan-action#208</a></li>
</ul>
<p><strong>Full Changelog</strong>: <a href="https://github.com/SonarSource/sonarqube-scan-action/compare/v5.3.1...v6.0.0">https://github.com/SonarSource/sonarqube-scan-action/compare/v5.3.1...v6.0.0</a></p>
<h2>v5.3.2</h2>
<p><strong>Full Changelog</strong>: <a href="https://github.com/SonarSource/sonarqube-scan-action/compare/v5.3.1...v5.3.2">https://github.com/SonarSource/sonarqube-scan-action/compare/v5.3.1...v5.3.2</a></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>fd88b7d</code></a> SQSCANGHA-119 New Readme structure</li>
<li><a href=""><code>27a157d</code></a> SQSCANGHA-118 Update the README to document the breaking change for args parsing</li>
<li><a href=""><code>e327da8</code></a> NO-JIRA Add documentation for contribution</li>
<li><a href=""><code>ff001fd</code></a> SQSCANGHA-107 Migrate install-build-wrapper</li>
<li><a href=""><code>a88c96d</code></a> SQSCANGHA-107 Make room for install-build-wrapper action</li>
<li><a href=""><code>a642810</code></a> SQSCANGHA-112 SQSCANGHA-113 Fixes from review and keytool refactor</li>
<li><a href=""><code>60aee70</code></a> NO-JIRA Disable fail fast on matrix jobs</li>
<li><a href=""><code>502204e</code></a> NO-JIRA Fix test assertion</li>
<li><a href=""><code>0b794a0</code></a> SQSCANGHA-112 Delete legacy shell script</li>
<li><a href=""><code>ece10df</code></a> SQSCANGHA-112 Extract installation step and other fixes</li>
<li>Additional commits viewable in <a href="https://github.com/sonarsource/sonarqube-scan-action/compare/v5.3.1...v6.0.0">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=SonarSource/sonarqube-scan-action&package-manager=github_actions&previous-version=5.3.1&new-version=6.0.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot merge` will merge this PR after your CI passes on it
- `@dependabot squash and merge` will squash and merge this PR after your CI passes on it
- `@dependabot cancel merge` will cancel a previously requested merge and block automerging
- `@dependabot reopen` will reopen this PR if it is closed
- `@dependabot close` will close this PR and stop Dependabot recreating it. You can achieve the same result by closing it manually
- `@dependabot show <dependency name> ignore conditions` will show all of the ignore conditions of the specified dependency
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `91951c1c55e7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.