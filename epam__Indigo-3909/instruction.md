# Issue

**Title:** Bump colord from 2.9.3 to 2.10.0 in /utils/indigo-service/frontend/ui

## Description

Bumps [colord](https://github.com/omgovich/colord) from 2.9.3 to 2.10.0.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/omgovich/colord/releases">colord's releases</a>.</em></p>
<blockquote>
<h2>v2.10 (RGB color mixing)</h2>
<ul>
<li><code>mix</code>, <code>tints</code>, <code>shades</code> and <code>tones</code> (<code>mix</code> plugin) now accept an optional interpolation color space. LAB stays the default; pass <code>&quot;rgb&quot;</code> to interpolate RGB channels instead — the way browsers and design tools (such as Figma) composite translucent layers.</li>
</ul>
<pre lang="js"><code>import { colord, extend } from &quot;colord&quot;;
import mixPlugin from &quot;colord/plugins/mix&quot;;
<p>extend([mixPlugin]);</p>
<p>colord(&quot;#ff0000&quot;).mix(&quot;#ffffff&quot;, 0.5, &quot;rgb&quot;).toHex(); // &quot;#ff8080&quot;
colord(&quot;#f0f3f1&quot;).mix(&quot;#007d40&quot;, 0.14, &quot;rgb&quot;).toHex(); // &quot;#cee2d8&quot; — same as compositing rgba(0, 125, 64, 0.14) over #f0f3f1
colord(&quot;#ff0000&quot;).tints(3, &quot;rgb&quot;).map((c) =&gt; c.toHex()); // [&quot;#ff0000&quot;, &quot;#ff8080&quot;, &quot;#ffffff&quot;]
</code></pre></p>
</blockquote>
</details>
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/omgovich/colord/blob/master/CHANGELOG.md">colord's changelog</a>.</em></p>
<blockquote>
<h3>2.10.0</h3>
<ul>
<li>Improve <code>mix</code> plugin by adding an optional <code>&quot;rgb&quot;</code> interpolation mode to <code>mix</code>, <code>tints</code>, <code>tones</code> and <code>shades</code></li>
</ul>
<h3>2.9.7</h3>
<ul>
<li>Make HEX parsing and serialization more than 2x faster</li>
</ul>
<h3>2.9.6</h3>
<ul>
<li>Fix: Rotate the unrounded hue so <code>rotate</code> and <code>harmonies</code> preserve the original color</li>
<li>Fix: Normalize HWB whiteness + blackness over 100% to gray ❤️ <a href="https://github.com/spokodev"><code>@​spokodev</code></a></li>
</ul>
<h3>2.9.5</h3>
<ul>
<li>Fix: Use adjusted chroma for the CIEDE2000 rotation term ❤️ <a href="https://github.com/maximilliangrand"><code>@​maximilliangrand</code></a></li>
<li>Fix: Keep the hue within <code>[0, 360)</code> in every color model ❤️ <a href="https://github.com/sarathfrancis90"><code>@​sarathfrancis90</code></a></li>
</ul>
<p>Both fixes change returned numbers for a small set of colors; <code>toHex()</code> output is unchanged. Snapshots holding <code>h: 360</code>, <code>&quot;hsl(360, …)&quot;</code> or a <code>delta()</code> value may need updating.</p>
<h3>2.9.4</h3>
<ul>
<li>Fix: Reject malformed color strings in linear time ❤️ <a href="https://github.com/GAP-dev"><code>@​GAP-dev</code></a></li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li>See full diff in <a href="https://github.com/omgovich/colord/commits/v2.10">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=colord&package-manager=npm_and_yarn&previous-version=2.9.3&new-version=2.10.0)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/epam/Indigo/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `95fda9af5f8a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.