# Issue

**Title:** Bump websocket-driver from 0.7.4 to 0.7.5 in /utils/indigo-service/frontend/ui

## Description

Bumps [websocket-driver](https://github.com/faye/websocket-driver-node) from 0.7.4 to 0.7.5.
<details>
<summary>Changelog</summary>
<p><em>Sourced from <a href="https://github.com/faye/websocket-driver-node/blob/main/CHANGELOG.md">websocket-driver's changelog</a>.</em></p>
<blockquote>
<h3>0.7.5 / 2026-06-04</h3>
<ul>
<li>Close a draft-75/76 connection if a length header grows to exceed the
configured max length</li>
<li>Fail the connection if a message is larger than the configured max length
after extension processing</li>
</ul>
</blockquote>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>5d6a9aa</code></a> Bump version to 0.7.5</li>
<li><a href=""><code>c55679a</code></a> Fail the connection if a message is larger than the configured max length aft...</li>
<li><a href=""><code>5b197ca</code></a> Close a draft-75/76 connection if a length header grows to exceed the configu...</li>
<li><a href=""><code>fc93a48</code></a> Test on Node v22, v24, and v26</li>
<li><a href=""><code>2e82d34</code></a> Test on recent versions of Node</li>
<li><a href=""><code>e4962db</code></a> Switch from Travis CI to GitHub Actions</li>
<li><a href=""><code>3f2f9b7</code></a> Travis update: cache npm modules, remove sudo, run on Node 15</li>
<li>See full diff in <a href="https://github.com/faye/websocket-driver-node/compare/0.7.4...0.7.5">compare view</a></li>
</ul>
</details>
<br />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `903b0f165b48`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.