# Issue

**Title:** chore(deps): bump dompurify from 3.2.5 to 3.3.1 in /frontend

## Description

Bumps [dompurify](https://github.com/cure53/DOMPurify) from 3.2.5 to 3.3.1.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/cure53/DOMPurify/releases">dompurify's releases</a>.</em></p>
<blockquote>
<h2>DOMPurify 3.3.1</h2>
<ul>
<li>Updated <code>ADD_FORBID_CONTENTS</code> setting to extend default list, thanks <a href="https://github.com/MariusRumpf"><code>@​MariusRumpf</code></a></li>
<li>Updated the ESM import syntax to be more correct, thanks <a href="https://github.com/binhpv"><code>@​binhpv</code></a></li>
</ul>
<h2>DOMPurify 3.3.0</h2>
<ul>
<li>Added the SVG <code>mask-type</code> attribute to default allow-list, thanks <a href="https://github.com/prasadrajandran"><code>@​prasadrajandran</code></a></li>
<li>Added support for <code>ADD_ATTR</code> and <code>ADD_TAGS</code> to accept functions, thanks <a href="https://github.com/nelstrom"><code>@​nelstrom</code></a></li>
<li>Fixed an issue with the <code>slot</code> element being in both SVG and HTML allow-list, thanks <a href="https://github.com/Wim-Valgaeren"><code>@​Wim-Valgaeren</code></a></li>
</ul>
<h2>DOMPurify 3.2.7</h2>
<ul>
<li>Added new attributes and elements to default allow-list, thanks <a href="https://github.com/elrion018"><code>@​elrion018</code></a></li>
<li>Added <code>tagName</code> parameter to custom element <code>attributeNameCheck</code>, thanks <a href="https://github.com/nelstrom"><code>@​nelstrom</code></a></li>
<li>Added better check for animated <code>href</code> attributes, thanks <a href="https://github.com/llamakko"><code>@​llamakko</code></a></li>
<li>Updated and improved the bundled types, thanks <a href="https://github.com/ssi02014"><code>@​ssi02014</code></a></li>
<li>Updated several tests to better align with new browser encoding behaviors</li>
<li>Improved the handling of potentially risky content inside CDATA elements, thanks <a href="https://github.com/securityMB"><code>@​securityMB</code></a> &amp; <a href="https://github.com/terjanq"><code>@​terjanq</code></a></li>
<li>Improved the regular expression for raw-text elements to cover textareas, thanks <a href="https://github.com/securityMB"><code>@​securityMB</code></a> &amp; <a href="https://github.com/terjanq"><code>@​terjanq</code></a></li>
</ul>
<h2>DOMPurify 3.2.6</h2>
<ul>
<li>Fixed several typos and removed clutter from our documentation, thanks <a href="https://github.com/Rotzbua"><code>@​Rotzbua</code></a></li>
<li>Added <code>matrix:</code> as an allowed URI scheme, thanks <a href="https://github.com/kleinesfilmroellchen"><code>@​kleinesfilmroellchen</code></a></li>
<li>Added better config hardening against prototype pollution, thanks <a href="https://github.com/EffectRenan"><code>@​EffectRenan</code></a></li>
<li>Added better handling of attribute removal, thanks <a href="https://github.com/michalnieruchalski-tiugo"><code>@​michalnieruchalski-tiugo</code></a></li>
<li>Added better configuration for aggressive mXSS scrubbing behavior, thanks <a href="https://github.com/BryanValverdeU"><code>@​BryanValverdeU</code></a></li>
<li>Removed the script that caused the fake entry <a href="https://security.snyk.io/vuln/SNYK-JS-DOMPURIFY-10176060">CVE-2025-48050</a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>6fc446a</code></a> Merge pull request <a href="">#1175</a> from cure53/main</li>
<li><a href=""><code>3b3bf91</code></a> Merge branch 'main' of github.com:cure53/DOMPurify</li>
<li><a href=""><code>9863f41</code></a> chore: Preparing 3.3.1 release</li>
<li><a href=""><code>b4e0295</code></a> chore: Preparing 3.3.0 release</li>
<li><a href=""><code>077746b</code></a> build(deps-dev): bump js-yaml from 4.1.0 to 4.1.1 (<a href="">#1170</a>)</li>
<li><a href=""><code>4de68bb</code></a> build(deps): bump actions/checkout from 5 to 6 (<a href="">#1171</a>)</li>
<li><a href=""><code>4c76b6f</code></a> Use correct ESM import syntax (<a href="">#1173</a>)</li>
<li><a href=""><code>27e8496</code></a> Merge pull request <a href="">#1168</a> from MariusRumpf/add-forbid-contents</li>
<li><a href=""><code>a920096</code></a> Add ADD_FORBID_CONTENTS setting to extend default list</li>
<li><a href=""><code>ac64660</code></a> Merge pull request <a href="">#1163</a> from cure53/dependabot/github_actions/actions/setup-...</li>
<li>Additional commits viewable in <a href="https://github.com/cure53/DOMPurify/compare/3.2.5...3.3.1">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=dompurify&package-manager=npm_and_yarn&previous-version=3.2.5&new-version=3.3.1)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/Steinbeck-Lab/cheminformatics-microservice/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cabce11becfd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.