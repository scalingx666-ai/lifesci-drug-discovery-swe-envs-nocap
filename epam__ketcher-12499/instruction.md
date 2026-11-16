# Issue

**Title:** chore(deps): bump qs and express

## Description

Bumps [qs](https://github.com/ljharb/qs) and [express](https://github.com/expressjs/express). These dependencies needed to be updated together.
Updates `qs` from 6.15.2 to 6.16.2
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/ljharb/qs/blob/main/CHANGELOG.md">qs's changelog</a>.</em></p>
<blockquote>
<h2><strong>6.16.2</strong></h2>
<ul>
<li>[Fix] <code>stringify</code>: encode keys when <code>allowEmptyArrays</code> is set (<a href="">#561</a>)</li>
<li>[meta] use double quotes for better OS support</li>
<li>[Dev Deps] update <code>evalmd</code>, <code>npmignore</code></li>
<li>[Tests] <code>stringify</code>: pin <code>allowEmptyArrays</code> output for keys that need no encoding</li>
</ul>
<h2><strong>6.16.1</strong></h2>
<ul>
<li>[Fix] <code>parse</code>: do not mutate an object input</li>
<li>[Fix] <code>stringify</code>: stop re-encoding structural separator dots when <code>encodeDotInKeys</code> is set (<a href="">#564</a>)</li>
<li>[Fix] <code>stringify</code>: <code>arrayFormat: 'comma'</code>: pass the full encoder arguments with <code>encodeValuesOnly</code></li>
<li>[Fix] <code>utils</code>: encode <code>+</code> as <code>%2B</code> in iso-8859-1 mode so values round-trip (<a href="">#565</a>)</li>
<li>[Fix] parse: only convert top-level dots to brackets when allowDots is on (<a href="">#621</a>)</li>
<li>[Fix] <code>stringify</code>: ignore inherited array format names (<a href="">#622</a>)</li>
<li>[Fix] <code>stringify</code>: <code>arrayFormat: 'comma'</code>: do not throw on elements with no callable <code>toString</code></li>
<li>[Fix] <code>utils</code>: <code>merge</code>: seed an overflow container's index from its own keys, not just the source</li>
<li>[Fix] <code>utils</code>: <code>merge</code>: keep a <code>strictMerge</code> conflict container's index and <code>arrayLimit</code> correct</li>
<li>[Fix] <code>parse</code>: only treat <code>[]</code> as array syntax when it ends the key</li>
<li>[Perf] <code>decode</code>: skip decoders when there is no percent sign (<a href="">#583</a>)</li>
<li>[Robustness] <code>utils</code>: <code>merge</code>: apply <code>arrayLimit</code> to the two-element array built for colliding values</li>
<li>[Robustness] <code>parse</code>: bound the nesting added by repeated <code>strictMerge</code> conflicts (credit <a href="https://github.com/Yeaseen"><code>@​Yeaseen</code></a>)</li>
<li>[Docs] document that <code>qs</code> and flat parsers disagree about parameter names</li>
<li>[Docs] clarify that <code>throwOnLimitExceeded</code> limits each array, not the total number of values</li>
<li>[Docs] clarify 6.14.1/6.15.2 parse bracket behavior change (<a href="">#567</a>, <a href="">#568</a>)</li>
<li>[meta] fix changelog indents</li>
<li>[actions] set least-privilege <code>cache-mode</code></li>
<li>[Tests] <code>utils</code>: <code>decode</code>: add missing cases</li>
<li>[Tests] <code>parse</code>: characterize the <code>]=</code> split when an <code>=</code> precedes any bracket group (<a href="">#620</a>)</li>
<li>[Tests] <code>parse</code>: <code>allowDots</code>: cover stray close brackets before a dot</li>
<li>[Dev Deps] update <code>@ljharb/eslint-config</code>, <code>eslint</code>, <code>tape</code></li>
</ul>
<h2><strong>6.16.0</strong></h2>
<ul>
<li>[New] <code>stringify</code>: add a <code>depth</code> option to bound recursion depth (default <code>Infinity</code>)</li>
<li>[Fix] stringify: serialize Date values when a filter is provided</li>
<li>[Fix] <code>parse</code>: enforce <code>arrayLimit</code> on comma groups under <code>[]=</code> when <code>throwOnLimitExceeded</code> is set</li>
<li>[Fix] <code>parse</code>: flatten a collection appended to an overflowed array (<a href="">#571</a>)</li>
<li>[Fix] <code>utils</code>: <code>isBuffer</code>: do not invoke a non-callable <code>constructor.isBuffer</code></li>
<li>[Fix] <code>stringify</code>: do not let <code>allowEmptyArrays</code> skip cycle detection (or drop own keys) on an empty array with own properties</li>
<li>[Fix] <code>stringify</code>: encode dots in a top-level key with a primitive value when encodeDotInKeys is set (<a href="">#562</a>)</li>
<li>[Docs] threat model: clarify <code>stringify</code> deep-nesting DoS is caller-bounded</li>
<li>[Docs] clarify <code>arrayLimit</code> is a representation threshold, not an element-count cap</li>
<li>[Tests] <code>parse</code>: remove a test that pinned <code>[]=</code> comma groups escaping <code>arrayLimit</code></li>
<li>[Tests] <code>stringify</code>: pin current <code>encodeDotInKeys</code> separator-dot behavior</li>
<li>[Dev Deps] update <code>@ljharb/eslint-config</code>, <code>eslint</code></li>
<li>[Dev Deps] update <code>eslint</code>, <code>evalmd</code></li>
</ul>
<h2><strong>6.15.4</strong></h2>
<ul>
<li>[Fix] <code>stringify</code>: encode keys when <code>allowEmptyArrays</code> is set (<a href="">#561</a>)</li>
<li>[meta] use double quotes for better OS support</li>
<li>[Dev Deps] update <code>@ljharb/eslint-config</code>, <code>evalmd</code>, <code>npmignore</code>, <code>tape</code></li>
<li>[Tests] <code>stringify</code>: pin <code>allowEmptyArrays</code> output for keys that need no encoding</li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>136912a</code></a> v6.16.2</li>
<li><a href=""><code>6ed1c73</code></a> [Dev Deps] update <code>evalmd</code>, <code>npmignore</code></li>
<li><a href=""><code>a09bc29</code></a> [meta] use double quotes for better OS support</li>
<li><a href=""><code>5d3b1b9</code></a> [Fix] <code>stringify</code>: encode keys when <code>allowEmptyArrays</code> is set</li>
<li><a href=""><code>f13ec6c</code></a> [Tests] <code>stringify</code>: pin <code>allowEmptyArrays</code> output for keys that need no enco...</li>
<li><a href=""><code>2471b66</code></a> v6.16.1</li>
<li><a href=""><code>51f736e</code></a> [Docs] document that <code>qs</code> and flat parsers disagree about parameter names</li>
<li><a href=""><code>40239f7</code></a> [Dev Deps] update <code>tape</code></li>
<li><a href=""><code>d219359</code></a> [Fix] <code>parse</code>: do not mutate an object input</li>
<li><a href=""><code>98157dc</code></a> [Fix] <code>stringify</code>: stop re-encoding structural separator dots when `encodeDot...</li>
<li>Additional commits viewable in <a href="https://github.com/ljharb/qs/compare/v6.15.2...v6.16.2">compare view</a></li>
</ul>
</details>
<br />

Updates `express` from 4.22.2 to 4.22.3
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/expressjs/express/blob/v4.22.3/History.md">express's changelog</a>.</em></p>
<blockquote>
<h1>4.22.3</h1>
<ul>
<li>Allow conditional revalidation for QUERY requests
<ul>
<li><code>req.fresh</code> now includes QUERY in the freshness check, so QUERY responses can return 304 when a validator matches</li>
</ul>
</li>
<li>deps: qs@~6.16.0</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>899b524</code></a> 4.22.3 (<a href="">#7466</a>)</li>
<li><a href=""><code>1fad2c3</code></a> ci: add npm staged publication with dist-tag support (<a href="">#7465</a>)</li>
<li><a href=""><code>4138650</code></a> deps: qs@~6.16.0 (<a href="">#7440</a>)</li>
<li><a href=""><code>61ccf2e</code></a> feat: allow conditional revalidation for QUERY requests (v4) (<a href="">#7377</a>)</li>
<li><a href=""><code>715101b</code></a> Update path-to-regexp to 0.1.13 because CVE-2026-4867 (<a href="">#7135</a>)</li>
<li><a href=""><code>f472e5f</code></a> docs: fix the release date format for 4.22.2</li>
<li>See full diff in <a href="https://github.com/expressjs/express/compare/v4.22.2...v4.22.3">compare view</a></li>
</ul>
</details>
<details>
<summary>Maintainer changes</summary>
<p>This version was pushed to npm by <a href="https://www.npmjs.com/~GitHub%20Actions">GitHub Actions</a>, a new releaser for express since your current version.</p>
</details>
<br />

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/epam/ketcher/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `09d9da19c905`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.