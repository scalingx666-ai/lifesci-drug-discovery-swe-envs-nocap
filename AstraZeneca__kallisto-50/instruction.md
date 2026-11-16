# Issue

**Title:** Bump gitpython from 3.1.36 to 3.1.41

## Description

Bumps [gitpython](https://github.com/gitpython-developers/GitPython) from 3.1.36 to 3.1.41.
<details>
<summary>Release notes</summary>
<p><em>Sourced from <a href="https://github.com/gitpython-developers/GitPython/releases">gitpython's releases</a>.</em></p>
<blockquote>
<h2>3.1.41 - fix Windows security issue</h2>
<p>The details about the Windows security issue <a href="https://github.com/gitpython-developers/GitPython/security/advisories/GHSA-2mqj-m65w-jghx">can be found in this advisory</a>.</p>
<p>Special thanks go to <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> who reported the issue and fixed it in a single stroke, while being responsible for an incredible amount of improvements that he contributed over the last couple of months ❤️.</p>
<h2>What's Changed</h2>
<ul>
<li>Add <code>__all__</code> in git.exc by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1719</a></li>
<li>Set submodule update cadence to weekly by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1721</a></li>
<li>Never modify sys.path by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1720</a></li>
<li>Bump git/ext/gitdb from <code>8ec2390</code> to <code>ec58b7e</code> by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">gitpython-developers/GitPython#1722</a></li>
<li>Revise comments, docstrings, some messages, and a bit of code by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1725</a></li>
<li>Use zero-argument super() by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1726</a></li>
<li>Remove obsolete note in _iter_packed_refs by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1727</a></li>
<li>Reorganize test_util and make xfail marks precise by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1729</a></li>
<li>Clarify license and make module top comments more consistent by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1730</a></li>
<li>Deprecate compat.is_<!-- raw HTML omitted -->, rewriting all uses by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1732</a></li>
<li>Revise and restore some module docstrings by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1735</a></li>
<li>Make the rmtree callback Windows-only by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1739</a></li>
<li>List all non-passing tests in test summaries by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1740</a></li>
<li>Document some minor subtleties in test_util.py by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1749</a></li>
<li>Always read metadata files as UTF-8 in setup.py by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1748</a></li>
<li>Test native Windows on CI by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1745</a></li>
<li>Test macOS on CI by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1752</a></li>
<li>Let close_fds be True on all platforms by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1753</a></li>
<li>Fix IndexFile.from_tree on Windows by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1751</a></li>
<li>Remove unused TASKKILL fallback in AutoInterrupt by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1754</a></li>
<li>Don't return with operand when conceptually void by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1755</a></li>
<li>Group .gitignore entries by purpose by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1758</a></li>
<li>Adding dubious ownership handling by <a href="https://github.com/marioaag"><code>@​marioaag</code></a> in <a href="">gitpython-developers/GitPython#1746</a></li>
<li>Avoid brittle assumptions about preexisting temporary files in tests by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1759</a></li>
<li>Overhaul noqa directives by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1760</a></li>
<li>Clarify some Git.execute kill_after_timeout limitations by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1761</a></li>
<li>Bump actions/setup-python from 4 to 5 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">gitpython-developers/GitPython#1763</a></li>
<li>Don't install black on Cygwin by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1766</a></li>
<li>Extract all &quot;import gc&quot; to module level by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1765</a></li>
<li>Extract remaining local &quot;import gc&quot; to module level by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1768</a></li>
<li>Replace xfail with gc.collect in TestSubmodule.test_rename by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1767</a></li>
<li>Enable CodeQL by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1769</a></li>
<li>Replace some uses of the deprecated mktemp function by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1770</a></li>
<li>Bump github/codeql-action from 2 to 3 by <a href="https://github.com/dependabot"><code>@​dependabot</code></a> in <a href="">gitpython-developers/GitPython#1773</a></li>
<li>Run some Windows environment variable tests only on Windows by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1774</a></li>
<li>Fix TemporaryFileSwap regression where file_path could not be Path by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1776</a></li>
<li>Improve hooks tests by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1777</a></li>
<li>Fix if items of Index is of type PathLike by <a href="https://github.com/stegm"><code>@​stegm</code></a> in <a href="">gitpython-developers/GitPython#1778</a></li>
<li>Better document IterableObj.iter_items and improve some subclasses by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1780</a></li>
<li>Revert &quot;Don't install black on Cygwin&quot; by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1783</a></li>
<li>Add missing pip in $PATH on Cygwin CI by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1784</a></li>
<li>Shorten Iterable docstrings and put IterableObj first by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1785</a></li>
<li>Fix incompletely revised Iterable/IterableObj docstrings by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1786</a></li>
<li>Pre-deprecate setting Git.USE_SHELL by <a href="https://github.com/EliahKagan"><code>@​EliahKagan</code></a> in <a href="">gitpython-developers/GitPython#1782</a></li>
</ul>
<!-- raw HTML omitted -->
</blockquote>
<p>... (truncated)</p>
</details>
<details>
<summary>Commits</summary>
<ul>
<li><a href=""><code>f288738</code></a> bump patch level</li>
<li><a href=""><code>ef3192c</code></a> Merge pull request <a href="">#1792</a> from EliahKagan/popen</li>
<li><a href=""><code>1f3caa3</code></a> Further clarify comment in test_hook_uses_shell_not_from_cwd</li>
<li><a href=""><code>3eb7c2a</code></a> Move safer_popen from git.util to git.cmd</li>
<li><a href=""><code>c551e91</code></a> Extract shared logic for using Popen safely on Windows</li>
<li><a href=""><code>15ebb25</code></a> Clarify comment in test_hook_uses_shell_not_from_cwd</li>
<li><a href=""><code>f44524a</code></a> Avoid spurious &quot;location may have moved&quot; on Windows</li>
<li><a href=""><code>a42ea0a</code></a> Cover absent/no-distro bash.exe in hooks &quot;not from cwd&quot; test</li>
<li><a href=""><code>7751436</code></a> Extract venv management from test_installation</li>
<li><a href=""><code>66ff4c1</code></a> Omit CWD in search for bash.exe to run hooks on Windows</li>
<li>Additional commits viewable in <a href="https://github.com/gitpython-developers/GitPython/compare/3.1.36...3.1.41">compare view</a></li>
</ul>
</details>
<br />

[![Dependabot compatibility score](https://dependabot-badges.githubapp.com/badges/compatibility_score?dependency-name=gitpython&package-manager=pip&previous-version=3.1.36&new-version=3.1.41)](https://docs.github.com/en/github/managing-security-vulnerabilities/about-dependabot-security-updates#about-compatibility-scores)

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
You can disable automated security fix PRs for this repo from the [Security Alerts page](https://github.com/AstraZeneca/kallisto/network/alerts).

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bd8098c7eae6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.