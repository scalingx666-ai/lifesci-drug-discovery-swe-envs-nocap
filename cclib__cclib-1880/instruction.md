# Issue

**Title:** Update pypa/gh-action-pypi-publish action to v1.14.2

## Description

This PR contains the following updates:

| Package | Type | Update | Change |
|---|---|---|---|
| [pypa/gh-action-pypi-publish](https://redirect.github.com/pypa/gh-action-pypi-publish) | action | patch | `v1.14.1` → `v1.14.2` |

---

### Release Notes

<details>
<summary>pypa/gh-action-pypi-publish (pypa/gh-action-pypi-publish)</summary>

### [`v1.14.2`](https://redirect.github.com/pypa/gh-action-pypi-publish/releases/tag/v1.14.2)

[Compare Source](https://redirect.github.com/pypa/gh-action-pypi-publish/compare/v1.14.1...v1.14.2)

<p align="right"><i>This one probably won't touch you visibly so just bookmark <a href="https://ep2026.europython.eu/session/defending-open-source-from-ai-slop-a-maintainer-s-practical-guide">@&#8203;webknjaz's EuroPython 2026 “AI” slop rant for when it's published on YouTube</a> or <a href="https://redirect.github.com/sponsors/webknjaz">encourage him to come back with more to share next year</a>!</i></p>

#### 🛠️ Urgh… Another release!? Again? Explain yourself!

Looking at the diff, you'll only witness updates across the dependency tree. That's it! It's not a security fix or anything like that even, no. But you'll want this update.

> \[!tip]
> So what *most* people will find useful is [@&#8203;takluyver](https://redirect.github.com/takluyver)[💰](https://redirect.github.com/sponsors/takluyver)'s update of Twine to v7 that we use internally (). This version will let them upload their sdists and wheels containing core packaging metadata v2.5 to (Test)PyPI.

#### 🧐 Tell me why..

<details>

<summary>
The rest of the updates bump things related to <code>pypi-attestations</code> and <code>sigstore</code>, which has the most interesting backstory here. @&#8203;facutuesca<a href="https://redirect.github.com/sponsors/facutuesca">💰</a> sent a patch in #&#8203;417 but a bunch more helped out.
</summary>

TL;DR non-pure-python projects with C-extensions tend to have dozens (sometimes hundreds) wheels to upload to PyPI per release. They are often quite big and take time to transfer over the network. People started noticing problems and coming up with DIY sharding workarounds like  around July 23.
On this date, projects with a good amount of bytes to publish would start getting timeouts 5 minutes after the PyPI publishing job begun. The same job that worked just fine before.

I had to start pinging upstream library and ecosystem people, on GitHub and privately, to start making sense of what was happening. Eventually, we collectively concluded that GitHub must've shortened the lifetime of their OIDC identity — it seems to have used to be 10 minutes long (at some point in the past) and is now 5 minutes, apparently. It's not documented clearly, and we have not been able to get any clarity by attempting to contact GitHub through private channels, using personal connections.

Over the course of investigation, [@&#8203;facutuesca](https://redirect.github.com/facutuesca)[💰](https://redirect.github.com/sponsors/facutuesca) found and fixed a related underlying cache invalidation bug in , which he then coordinated propagation through the dependency chain updates in sigstore-python, pypi-attestations, gh-action-pypi-publish and gh-action-sigstore-python.

Mike's also discovered that Sigstore's Rekor slowdown seems to have become the main contributing cause of the last week's incident. He's collected some data to support this claim: <https://publishing-five-minute-timeout.tiiny.site>.

<center>
  <a href="https://xkcd.com/2549/">
    <img src="https://imgs.xkcd.com/comics/edge_cake_2x.png" alt="Edge Cake XKCD feels just like this release">
  </a>
</center>

</details>

#### 🫶 New Contributors

- [@&#8203;davidbrochart](https://redirect.github.com/davidbrochart) made their first contribution in
- [@&#8203;takluyver](https://redirect.github.com/takluyver) made their first contribution in

**🪞 Full Diff**: <https://github.com/pypa/gh-action-pypi-publish/compare/v1.14.1...v1.14.2>

**🧔‍♂️ Release Manager:** [@&#8203;webknjaz](https://redirect.github.com/sponsors/webknjaz) [🇺🇦](https://stand-with-ukraine.pp.ua)

**🙏 Special Thanks** to [@&#8203;davidbrochart](https://redirect.github.com/davidbrochart)[💰](https://redirect.github.com/sponsors/davidbrochart) and [@&#8203;Dreamsorcerer](https://redirect.github.com/Dreamsorcerer)[💰](https://redirect.github.com/sponsors/Dreamsorcerer) for turning my attention (in  and in private) to the newly surfaced corner case in GitHub's behavior that only affected a narrow category of projects while many others remained blissfully unaware. [@&#8203;bdraco](https://redirect.github.com/bdraco)[💰](https://redirect.github.com/sponsors/bdraco) came up with a DIY sharding workaround for aiohttp that served as a demo for other projects. [@&#8203;miketheman](https://redirect.github.com/miketheman)[💰](https://redirect.github.com/sponsors/miketheman) confirmed the Warehouse-side details. Also, [@&#8203;jku](https://redirect.github.com/jku)[💰](https://redirect.github.com/sponsors/jku) and [@&#8203;woodruffw](https://redirect.github.com/woodruffw)[💰](https://redirect.github.com/sponsors/woodruffw) helped work through, review and release the Sigstore ecosystem upstream libs.

**💬 Discuss** [on Bluesky 🦋](https://bsky.app/profile/did:plc:ve6s3mxkefjaxty3m4fdqumn/post/3mrsqy2xba22j), [on Mastodon 🐘](https://mastodon.social/@&#8203;webknjaz/117005132816750073) and [on GitHub][release discussion].

[![GH Sponsors badge]][GH Sponsors URL]

[GH Sponsors badge]: https://img.shields.io/badge/%40webknjaz-transparent?logo=githubsponsors&logoColor=%23EA4AAA&label=Sponsor&color=2a313c

[GH Sponsors URL]: https://redirect.github.com/sponsors/webknjaz

[release discussion]: https://redirect.github.com/pypa/gh-action-pypi-publish/discussions/419

</details>

---

### Configuration

📅 **Schedule**: (UTC)

- Branch creation
  - At any time (no schedule defined)
- Automerge
  - At any time (no schedule defined)

🚦 **Automerge**: Enabled.

♻ **Rebasing**: Whenever PR is behind base branch, or you tick the rebase/retry checkbox.

🔕 **Ignore**: Close this PR and you won't be reminded about this update again.

---

 - [ ] <!-- rebase-check -->If you want to rebase/retry this PR, check this box

---

This PR was generated by [Mend Renovate](https://mend.io/renovate/). View the [repository job log](https://developer.mend.io/github/cclib/cclib).
<!--renovate-debug:eyJjcmVhdGVkSW5WZXIiOiI0My4yODAuMCIsInVwZGF0ZWRJblZlciI6IjQ0LjMuMiIsInRhcmdldEJyYW5jaCI6Im1hc3RlciIsImxhYmVscyI6WyJkZXBlbmRlbmNpZXMiLCJnaXRodWJfYWN0aW9ucyJdfQ==-->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `134cedf49e03`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.