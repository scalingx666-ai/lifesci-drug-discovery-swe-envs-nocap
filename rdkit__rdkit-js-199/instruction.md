# Issue

**Title:** Bump typescript from 4.8.3 to 4.8.4

## Description

Bumps [typescript](https://github.com/Microsoft/TypeScript) from 4.8.3 to 4.8.4.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/Microsoft/TypeScript/releases">typescript's releases</a>.</em></p>
<blockquote>
<h2>TypeScript 4.8.4</h2>
<p>For release notes, check out the <a href="https://devblogs.microsoft.com/typescript/announcing-typescript-4-8/">release announcement</a>.</p>
<p>For the complete list of fixed issues, check out the</p>
<ul>
<li><a href="https://github.com/microsoft/TypeScript/issues?q=milestone%3A%22TypeScript+4.8.0%22+">fixed issues query for Typescript 4.8.0 (Beta)</a>.</li>
<li><a href="https://github.com/microsoft/TypeScript/issues?q=milestone%3A%22TypeScript+4.8.1%22+">fixed issues query for Typescript 4.8.1 (RC)</a>.</li>
<li><a href="https://github.com/microsoft/TypeScript/issues?q=milestone%3A%22TypeScript+4.8.2%22+">fixed issues query for Typescript 4.8.2 (Stable)</a>.</li>
<li><a href="https://github.com/microsoft/TypeScript/issues?q=milestone%3A%22TypeScript+4.8.3%22+">fixed issues query for Typescript 4.8.3 (Stable)</a>.</li>
<li><a href="https://github.com/microsoft/TypeScript/issues?q=milestone%3A%22TypeScript+4.8.4%22+">fixed issues query for Typescript 4.8.4 (Stable)</a>.</li>
</ul>
<p>Downloads are available on:</p>
<ul>
<li><a href="https://www.npmjs.com/package/typescript">npm</a></li>
<li><a href="https://marketplace.visualstudio.com/items?itemName=TypeScriptTeam.TypeScript-484">Visual Studio 2022/2019</a> (<a href="https://github.com/Microsoft/TypeScript/wiki/Updating-TypeScript-in-Visual-Studio-2017">Select new version in project options</a>)</li>
<li><a href="https://www.nuget.org/packages/Microsoft.TypeScript.MSBuild">NuGet package</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>a614119</code></a> Bump version to 4.8.4 and LKG</li>
<li><a href=""><code>369b4d8</code></a> Cherry pick <a href="https://github-redirect.dependabot.com/Microsoft/TypeScript/issues/50537">#50537</a> and <a href="https://github-redirect.dependabot.com/Microsoft/TypeScript/issues/50779">#50779</a> to release-4.8 (<a href="https://github-redirect.dependabot.com/Microsoft/TypeScript/issues/50907">#50907</a>)</li>
<li><a href=""><code>41e1ade</code></a> Cherry-pick PR <a href="https://github-redirect.dependabot.com/Microsoft/TypeScript/issues/50704">#50704</a> into release-4.8 (<a href="https://github-redirect.dependabot.com/Microsoft/TypeScript/issues/50741">#50741</a>)</li>
<li><a href=""><code>2acf3a3</code></a> Cherry-pick PR <a href="https://github-redirect.dependabot.com/Microsoft/TypeScript/issues/50691">#50691</a> into release-4.8 (<a href="https://github-redirect.dependabot.com/Microsoft/TypeScript/issues/50743">#50743</a>)</li>
<li><a href=""><code>39576e6</code></a> Cherry-pick PR <a href="https://github-redirect.dependabot.com/Microsoft/TypeScript/issues/50673">#50673</a> into release-4.8 (<a href="https://github-redirect.dependabot.com/Microsoft/TypeScript/issues/50742">#50742</a>)</li>
<li><a href=""><code>5773723</code></a> Cherry-pick <a href="https://github-redirect.dependabot.com/Microsoft/TypeScript/issues/50724">#50724</a> to release-4.8 (<a href="https://github-redirect.dependabot.com/Microsoft/TypeScript/issues/50760">#50760</a>)</li>
<li><a href=""><code>a3b3555</code></a> Cherry-pick PR <a href="https://github-redirect.dependabot.com/Microsoft/TypeScript/issues/50797">#50797</a> into release-4.8 (<a href="https://github-redirect.dependabot.com/Microsoft/TypeScript/issues/50798">#50798</a>)</li>
<li><a href=""><code>bb8cf90</code></a> Handle more places where package direcroy is converted to canonical file path...</li>
<li>See full diff in <a href="https://github.com/Microsoft/TypeScript/compare/v4.8.3...v4.8.4">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=typescript&package-manager=npm_and_yarn&previous-version=4.8.3&new-version=4.8.4)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
- `@dependabot ignore this major version` will close this PR and stop Dependabot creating any more for this major version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this minor version` will close this PR and stop Dependabot creating any more for this minor version (unless you reopen the PR or upgrade to it yourself)
- `@dependabot ignore this dependency` will close this PR and stop Dependabot creating any more for this dependency (unless you reopen the PR or upgrade to it yourself)

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b065dd55b09`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.