# Issue

**Title:** Bump @typescript-eslint/parser from 5.43.0 to 5.45.0

## Description

Bumps [@typescript-eslint/parser](https://github.com/typescript-eslint/typescript-eslint/tree/HEAD/packages/parser) from 5.43.0 to 5.45.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/typescript-eslint/typescript-eslint/releases"><code>@​typescript-eslint/parser</code>'s releases</a>.</em></p>
<blockquote>
<h2>v5.45.0</h2>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.44.0...v5.45.0">5.45.0</a> (2022-11-28)</h1>
<h3>Bug Fixes</h3>
<ul>
<li><strong>eslint-plugin:</strong> [array-type] --fix flag removes parentheses from type (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5997">#5997</a>) (<a href="">42b33af</a>)</li>
<li><strong>eslint-plugin:</strong> [keyword-spacing] prevent crash on no options (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6073">#6073</a>) (<a href="">1f19998</a>)</li>
<li><strong>eslint-plugin:</strong> [member-ordering] support private fields (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5859">#5859</a>) (<a href="">f02761a</a>)</li>
<li><strong>eslint-plugin:</strong> [prefer-readonly] report if a member's property is reassigned (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6043">#6043</a>) (<a href="">6e079eb</a>)</li>
<li><strong>scope-manager:</strong> add support for TS4.9 satisfies expression (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6059">#6059</a>) (<a href="">44027db</a>)</li>
<li><strong>typescript-estree:</strong> stub out <code>ts.SatisfiesExpression</code> on old TS versions (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/6076">#6076</a>) (<a href="">1302b30</a>)</li>
</ul>
<h3>Features</h3>
<ul>
<li><strong>eslint-plugin:</strong> [member-ordering] add a required option for required vs. optional member ordering (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5965">#5965</a>) (<a href="">2abadc6</a>)</li>
<li>support Auto Accessor syntax (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5926">#5926</a>) (<a href="">becd1f8</a>)</li>
</ul>
<h2>v5.44.0</h2>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.43.0...v5.44.0">5.44.0</a> (2022-11-21)</h1>
<h3>Bug Fixes</h3>
<ul>
<li><strong>eslint-plugin:</strong> [no-empty-interface] disable autofix for declaration merging with class (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5920">#5920</a>) (<a href="">a4f85b8</a>)</li>
<li><strong>eslint-plugin:</strong> [no-unnecessary-condition] handle index signature type (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5912">#5912</a>) (<a href="">5baad08</a>)</li>
<li><strong>eslint-plugin:</strong> [prefer-optional-chain] handle binary expressions in negated or (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5992">#5992</a>) (<a href="">2778ff0</a>)</li>
<li><strong>typescript-estree:</strong> don't consider a cached program unless it's specified in the current <code>parserOptions.project</code> config (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5999">#5999</a>) (<a href="">530e0e6</a>)</li>
</ul>
<h3>Features</h3>
<ul>
<li><strong>eslint-plugin:</strong> [adjacent-overload-signatures] check BlockStatement nodes (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5998">#5998</a>) (<a href="">97d3e56</a>)</li>
<li><strong>eslint-plugin:</strong> [keyword-spacing] Support spacing in import-type syntax (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5977">#5977</a>) (<a href="">6a735e1</a>)</li>
<li>support parsing <code>satisfies</code> operators (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5717">#5717</a>) (<a href="">20d7cae</a>)</li>
<li>update to TypeScript 4.9 (<a href="https://github-redirect.dependabot.com/typescript-eslint/typescript-eslint/issues/5716">#5716</a>) (<a href="">4d744ea</a>)</li>
</ul>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/typescript-eslint/typescript-eslint/blob/main/packages/parser/CHANGELOG.md"><code>@​typescript-eslint/parser</code>'s changelog</a>.</em></p>
<blockquote>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.44.0...v5.45.0">5.45.0</a> (2022-11-28)</h1>
<p><strong>Note:</strong> Version bump only for package <code>@​typescript-eslint/parser</code></p>
<h1><a href="https://github.com/typescript-eslint/typescript-eslint/compare/v5.43.0...v5.44.0">5.44.0</a> (2022-11-21)</h1>
<p><strong>Note:</strong> Version bump only for package <code>@​typescript-eslint/parser</code></p>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>267da4e</code></a> chore: publish v5.45.0</li>
<li><a href=""><code>01159d2</code></a> chore: publish v5.44.0</li>
<li><a href=""><code>426c2f9</code></a> chore: remove unnecessary project names from nx commands (<a href="">#6054</a>)</li>
<li><a href=""><code>e2d1263</code></a> chore: switched repo lint to use nx run-many (<a href="">#6038</a>)</li>
<li>See full diff in <a href="https://github.com/typescript-eslint/typescript-eslint/commits/v5.45.0/packages/parser">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=@typescript-eslint/parser&package-manager=npm_and_yarn&previous-version=5.43.0&new-version=5.45.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bbde39e23238`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.