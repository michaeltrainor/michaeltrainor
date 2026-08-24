# AGENTS.md

## Project overview

This repository is the **GitHub profile README** for the user `mtd3v` (`michaeltrainor/michaeltrainor`).
It is a "special" GitHub repo whose `README.md` renders on the GitHub profile page.

It contains only:
- `README.md` — the profile content (Markdown).
- `background.jpg` — image referenced by the README.

There is no application source, package build, or automated test suite. The "product" is the
rendered profile page.

## Cursor Cloud specific instructions

- There is nothing to compile, no test suite, and no lint config. Development work here means editing
  `README.md` (and occasionally `background.jpg`) and verifying it renders correctly.
- The only dev dependency is `grip` (GitHub Readme Instant Preview), which renders Markdown locally
  the same way GitHub does. It is installed into the user site by the startup update script
  (`pip3 install --user --break-system-packages grip`) and its executable lives in `~/.local/bin`,
  which is not on `PATH` by default — prefix commands with `export PATH="$HOME/.local/bin:$PATH"`.
- Run the live preview server (dev workflow):
  `export PATH="$HOME/.local/bin:$PATH"; grip README.md 0.0.0.0:6419`
  then open `http://localhost:6419/`. It live-reloads on save.
- Export a static HTML render instead: `grip --export README.md out.html`.
- `grip` fetches GitHub's Markdown rendering + CSS over the network and caches them under
  `~/.grip/cache-*`. The first render needs outbound access to `github.com` /
  `github.githubassets.com`; subsequent renders use the cache. If GitHub API rate limits are hit,
  authenticate with `grip --user <user> --pass <token>`.
