# Issue

**Title:** Bump github/codeql-action from 2 to 4

## Description

Bumps [github/codeql-action](https://github.com/github/codeql-action) from 2 to 4.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/github/codeql-action/releases">github/codeql-action's releases</a>.</em></p>
<blockquote>
<h2>v3.35.1</h2>
<ul>
<li>Fix incorrect minimum required Git version for <a href="">improved incremental analysis</a>: it should have been 2.36.0, not 2.11.0. <a href="">#3781</a></li>
</ul>
<h2>v3.35.0</h2>
<ul>
<li>Reduced the minimum Git version required for <a href="">improved incremental analysis</a> from 2.38.0 to 2.11.0. <a href="">#3767</a></li>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.25.1">2.25.1</a>. <a href="">#3773</a></li>
</ul>
<h2>v3.34.1</h2>
<ul>
<li>Downgrade default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.24.3">2.24.3</a> due to issues with a small percentage of Actions and JavaScript analyses. <a href="">#3762</a></li>
</ul>
<h2>v3.34.0</h2>
<ul>
<li>Added an experimental change which disables TRAP caching when <a href="">improved incremental analysis</a> is enabled, since improved incremental analysis supersedes TRAP caching. This will improve performance and reduce Actions cache usage. We expect to roll this change out to everyone in March. <a href="">#3569</a></li>
<li>We are rolling out improved incremental analysis to C/C++ analyses that use build mode <code>none</code>. We expect this rollout to be complete by the end of April 2026. <a href="">#3584</a></li>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.25.0">2.25.0</a>. <a href="">#3585</a></li>
</ul>
<h2>v3.33.0</h2>
<ul>
<li>Upcoming change: Starting April 2026, the CodeQL Action will skip collecting file coverage information on pull requests to improve analysis performance. File coverage information will still be computed on non-PR analyses. Pull request analyses will log a warning about this upcoming change. <a href="">#3562</a>
To opt out of this change:
<ul>
<li><strong>Repositories owned by an organization:</strong> Create a custom repository property with the name <code>github-codeql-file-coverage-on-prs</code> and the type &quot;True/false&quot;, then set this property to <code>true</code> in the repository's settings. For more information, see <a href="https://docs.github.com/en/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization">Managing custom properties for repositories in your organization</a>. Alternatively, if you are using an advanced setup workflow, you can set the <code>CODEQL_ACTION_FILE_COVERAGE_ON_PRS</code> environment variable to <code>true</code> in your workflow.</li>
<li><strong>User-owned repositories using default setup:</strong> Switch to an advanced setup workflow and set the <code>CODEQL_ACTION_FILE_COVERAGE_ON_PRS</code> environment variable to <code>true</code> in your workflow.</li>
<li><strong>User-owned repositories using advanced setup:</strong> Set the <code>CODEQL_ACTION_FILE_COVERAGE_ON_PRS</code> environment variable to <code>true</code> in your workflow.</li>
</ul>
</li>
<li>Fixed <a href="">a bug</a> which caused the CodeQL Action to fail loading repository properties if a &quot;Multi select&quot; repository property was configured for the repository. <a href="">#3557</a></li>
<li>The CodeQL Action now loads <a href="https://docs.github.com/en/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization">custom repository properties</a> on GitHub Enterprise Server, enabling the customization of features such as <code>github-codeql-disable-overlay</code> that was previously only available on GitHub.com. <a href="">#3559</a></li>
<li>Once <a href="https://docs.github.com/en/code-security/how-tos/secure-at-scale/configure-organization-security/manage-usage-and-access/giving-org-access-private-registries">private package registries</a> can be configured with OIDC-based authentication for organizations, the CodeQL Action will now be able to accept such configurations. <a href="">#3563</a></li>
<li>Fixed the retry mechanism for database uploads. Previously this would fail with the error &quot;Response body object should not be disturbed or locked&quot;. <a href="">#3564</a></li>
<li>A warning is now emitted if the CodeQL Action detects a repository property whose name suggests that it relates to the CodeQL Action, but which is not one of the properties recognised by the current version of the CodeQL Action. <a href="">#3570</a></li>
</ul>
<h2>v3.32.6</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.24.3">2.24.3</a>. <a href="">#3548</a></li>
</ul>
<h2>v3.32.5</h2>
<ul>
<li>Repositories owned by an organization can now set up the <code>github-codeql-disable-overlay</code> custom repository property to disable <a href="">improved incremental analysis for CodeQL</a>. First, create a custom repository property with the name <code>github-codeql-disable-overlay</code> and the type &quot;True/false&quot; in the organization's settings. Then in the repository's settings, set this property to <code>true</code> to disable improved incremental analysis. For more information, see <a href="https://docs.github.com/en/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization">Managing custom properties for repositories in your organization</a>. This feature is not yet available on GitHub Enterprise Server. <a href="">#3507</a></li>
<li>Added an experimental change so that when <a href="">improved incremental analysis</a> fails on a runner — potentially due to insufficient disk space — the failure is recorded in the Actions cache so that subsequent runs will automatically skip improved incremental analysis until something changes (e.g. a larger runner is provisioned or a new CodeQL version is released). We expect to roll this change out to everyone in March. <a href="">#3487</a></li>
<li>The minimum memory check for improved incremental analysis is now skipped for CodeQL 2.24.3 and later, which has reduced peak RAM usage. <a href="">#3515</a></li>
<li>Reduced log levels for best-effort private package registry connection check failures to reduce noise from workflow annotations. <a href="">#3516</a></li>
<li>Added an experimental change which lowers the minimum disk space requirement for <a href="">improved incremental analysis</a>, enabling it to run on standard GitHub Actions runners. We expect to roll this change out to everyone in March. <a href="">#3498</a></li>
<li>Added an experimental change which allows the <code>start-proxy</code> action to resolve the CodeQL CLI version from feature flags instead of using the linked CLI bundle version. We expect to roll this change out to everyone in March. <a href="">#3512</a></li>
<li>The previously experimental changes from versions 4.32.3, 4.32.4, 3.32.3 and 3.32.4 are now enabled by default. <a href="">#3503</a>, <a href="">#3504</a></li>
</ul>
<h2>v3.32.4</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.24.2">2.24.2</a>. <a href="">#3493</a></li>
<li>Added an experimental change which improves how certificates are generated for the authentication proxy that is used by the CodeQL Action in Default Setup when <a href="https://docs.github.com/en/code-security/how-tos/secure-at-scale/configure-organization-security/manage-usage-and-access/giving-org-access-private-registries">private package registries are configured</a>. This is expected to generate more widely compatible certificates and should have no impact on analyses which are working correctly already. We expect to roll this change out to everyone in February. <a href="">#3473</a></li>
<li>When the CodeQL Action is run <a href="https://docs.github.com/en/code-security/how-tos/scan-code-for-vulnerabilities/troubleshooting/troubleshooting-analysis-errors/logs-not-detailed-enough#creating-codeql-debugging-artifacts-for-codeql-default-setup">with debugging enabled in Default Setup</a> and <a href="https://docs.github.com/en/code-security/how-tos/secure-at-scale/configure-organization-security/manage-usage-and-access/giving-org-access-private-registries">private package registries are configured</a>, the &quot;Setup proxy for registries&quot; step will output additional diagnostic information that can be used for troubleshooting. <a href="">#3486</a></li>
<li>Added a setting which allows the CodeQL Action to enable network debugging for Java programs. This will help GitHub staff support customers with troubleshooting issues in GitHub-managed CodeQL workflows, such as Default Setup. This setting can only be enabled by GitHub staff. <a href="">#3485</a></li>
<li>Added a setting which enables GitHub-managed workflows, such as Default Setup, to use a <a href="https://github.com/dsp-testing/codeql-cli-nightlies">nightly CodeQL CLI release</a> instead of the latest, stable release that is used by default. This will help GitHub staff support customers whose analyses for a given repository or organization require early access to a change in an upcoming CodeQL CLI release. This setting can only be enabled by GitHub staff. <a href="">#3484</a></li>
</ul>
<h2>v3.32.3</h2>
<ul>
<li>Added experimental support for testing connections to <a href="https://docs.github.com/en/code-security/how-tos/secure-at-scale/configure-organization-security/manage-usage-and-access/giving-org-access-private-registries">private package registries</a>. This feature is not currently enabled for any analysis. In the future, it may be enabled by default for Default Setup. <a href="">#3466</a></li>
</ul>
<h2>v3.32.2</h2>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/github/codeql-action/blob/main/CHANGELOG.md">github/codeql-action's changelog</a>.</em></p>
<blockquote>
<h2>4.35.1 - 27 Mar 2026</h2>
<ul>
<li>Fix incorrect minimum required Git version for <a href="">improved incremental analysis</a>: it should have been 2.36.0, not 2.11.0. <a href="">#3781</a></li>
</ul>
<h2>4.35.0 - 27 Mar 2026</h2>
<ul>
<li>Reduced the minimum Git version required for <a href="">improved incremental analysis</a> from 2.38.0 to 2.11.0. <a href="">#3767</a></li>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.25.1">2.25.1</a>. <a href="">#3773</a></li>
</ul>
<h2>4.34.1 - 20 Mar 2026</h2>
<ul>
<li>Downgrade default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.24.3">2.24.3</a> due to issues with a small percentage of Actions and JavaScript analyses. <a href="">#3762</a></li>
</ul>
<h2>4.34.0 - 20 Mar 2026</h2>
<ul>
<li>Added an experimental change which disables TRAP caching when <a href="">improved incremental analysis</a> is enabled, since improved incremental analysis supersedes TRAP caching. This will improve performance and reduce Actions cache usage. We expect to roll this change out to everyone in March. <a href="">#3569</a></li>
<li>We are rolling out improved incremental analysis to C/C++ analyses that use build mode <code>none</code>. We expect this rollout to be complete by the end of April 2026. <a href="">#3584</a></li>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.25.0">2.25.0</a>. <a href="">#3585</a></li>
</ul>
<h2>4.33.0 - 16 Mar 2026</h2>
<ul>
<li>
<p>Upcoming change: Starting April 2026, the CodeQL Action will skip collecting file coverage information on pull requests to improve analysis performance. File coverage information will still be computed on non-PR analyses. Pull request analyses will log a warning about this upcoming change. <a href="">#3562</a></p>
<p>To opt out of this change:</p>
<ul>
<li><strong>Repositories owned by an organization:</strong> Create a custom repository property with the name <code>github-codeql-file-coverage-on-prs</code> and the type &quot;True/false&quot;, then set this property to <code>true</code> in the repository's settings. For more information, see <a href="https://docs.github.com/en/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization">Managing custom properties for repositories in your organization</a>. Alternatively, if you are using an advanced setup workflow, you can set the <code>CODEQL_ACTION_FILE_COVERAGE_ON_PRS</code> environment variable to <code>true</code> in your workflow.</li>
<li><strong>User-owned repositories using default setup:</strong> Switch to an advanced setup workflow and set the <code>CODEQL_ACTION_FILE_COVERAGE_ON_PRS</code> environment variable to <code>true</code> in your workflow.</li>
<li><strong>User-owned repositories using advanced setup:</strong> Set the <code>CODEQL_ACTION_FILE_COVERAGE_ON_PRS</code> environment variable to <code>true</code> in your workflow.</li>
</ul>
</li>
<li>
<p>Fixed <a href="">a bug</a> which caused the CodeQL Action to fail loading repository properties if a &quot;Multi select&quot; repository property was configured for the repository. <a href="">#3557</a></p>
</li>
<li>
<p>The CodeQL Action now loads <a href="https://docs.github.com/en/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization">custom repository properties</a> on GitHub Enterprise Server, enabling the customization of features such as <code>github-codeql-disable-overlay</code> that was previously only available on GitHub.com. <a href="">#3559</a></p>
</li>
<li>
<p>Once <a href="https://docs.github.com/en/code-security/how-tos/secure-at-scale/configure-organization-security/manage-usage-and-access/giving-org-access-private-registries">private package registries</a> can be configured with OIDC-based authentication for organizations, the CodeQL Action will now be able to accept such configurations. <a href="">#3563</a></p>
</li>
<li>
<p>Fixed the retry mechanism for database uploads. Previously this would fail with the error &quot;Response body object should not be disturbed or locked&quot;. <a href="">#3564</a></p>
</li>
<li>
<p>A warning is now emitted if the CodeQL Action detects a repository property whose name suggests that it relates to the CodeQL Action, but which is not one of the properties recognised by the current version of the CodeQL Action. <a href="">#3570</a></p>
</li>
</ul>
<h2>4.32.6 - 05 Mar 2026</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.24.3">2.24.3</a>. <a href="">#3548</a></li>
</ul>
<h2>4.32.5 - 02 Mar 2026</h2>
<ul>
<li>Repositories owned by an organization can now set up the <code>github-codeql-disable-overlay</code> custom repository property to disable <a href="">improved incremental analysis for CodeQL</a>. First, create a custom repository property with the name <code>github-codeql-disable-overlay</code> and the type &quot;True/false&quot; in the organization's settings. Then in the repository's settings, set this property to <code>true</code> to disable improved incremental analysis. For more information, see <a href="https://docs.github.com/en/organizations/managing-organization-settings/managing-custom-properties-for-repositories-in-your-organization">Managing custom properties for repositories in your organization</a>. This feature is not yet available on GitHub Enterprise Server. <a href="">#3507</a></li>
<li>Added an experimental change so that when <a href="">improved incremental analysis</a> fails on a runner — potentially due to insufficient disk space — the failure is recorded in the Actions cache so that subsequent runs will automatically skip improved incremental analysis until something changes (e.g. a larger runner is provisioned or a new CodeQL version is released). We expect to roll this change out to everyone in March. <a href="">#3487</a></li>
<li>The minimum memory check for improved incremental analysis is now skipped for CodeQL 2.24.3 and later, which has reduced peak RAM usage. <a href="">#3515</a></li>
<li>Reduced log levels for best-effort private package registry connection check failures to reduce noise from workflow annotations. <a href="">#3516</a></li>
<li>Added an experimental change which lowers the minimum disk space requirement for <a href="">improved incremental analysis</a>, enabling it to run on standard GitHub Actions runners. We expect to roll this change out to everyone in March. <a href="">#3498</a></li>
<li>Added an experimental change which allows the <code>start-proxy</code> action to resolve the CodeQL CLI version from feature flags instead of using the linked CLI bundle version. We expect to roll this change out to everyone in March. <a href="">#3512</a></li>
<li>The previously experimental changes from versions 4.32.3, 4.32.4, 3.32.3 and 3.32.4 are now enabled by default. <a href="">#3503</a>, <a href="">#3504</a></li>
</ul>
<h2>4.32.4 - 20 Feb 2026</h2>
<ul>
<li>Update default CodeQL bundle version to <a href="https://github.com/github/codeql-action/releases/tag/codeql-bundle-v2.24.2">2.24.2</a>. <a href="">#3493</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>c10b806</code></a> Merge pull request <a href="">#3782</a> from github/update-v4.35.1-d6d1743b8</li>
<li><a href=""><code>c5ffd06</code></a> Update changelog for v4.35.1</li>
<li><a href=""><code>d6d1743</code></a> Merge pull request <a href="">#3781</a> from github/henrymercer/update-git-minimum-version</li>
<li><a href=""><code>65d2efa</code></a> Add changelog note</li>
<li><a href=""><code>2437b20</code></a> Update minimum git version for overlay to 2.36.0</li>
<li><a href=""><code>ea5f719</code></a> Merge pull request <a href="">#3775</a> from github/dependabot/npm_and_yarn/node-forge-1.4.0</li>
<li><a href=""><code>45ceeea</code></a> Merge pull request <a href="">#3777</a> from github/mergeback/v4.35.0-to-main-b8bb9f28</li>
<li><a href=""><code>24448c9</code></a> Rebuild</li>
<li><a href=""><code>7c51060</code></a> Update changelog and version after v4.35.0</li>
<li><a href=""><code>b8bb9f2</code></a> Merge pull request <a href="">#3776</a> from github/update-v4.35.0-0078ad667</li>
<li>Additional commits viewable in <a href="https://github.com/github/codeql-action/compare/v2...v4">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=github/codeql-action&package-manager=github_actions&previous-version=2&new-version=4)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5e7aa70171b0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.