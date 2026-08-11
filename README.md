# Justin Rhee

Hi. I'm a product designer building agent harnesses on OpenClaw and Claude Code, mostly by getting things wrong and then fixing them.

These small tools are what came out of that. Every one of them exists because something broke, I lost time to it, and I wanted to make sure it couldn't happen the same way twice.

## What I've been building

The tools all came out of one setup: a way of working where agents write the code and plain scripts, not models, decide when it's actually done.

A plan gets written, then a model from a different vendor gets asked to tear it apart rather than approve it. A cheap model does the typing in a jail with no shell and no network. Deterministic checks run before any of it reaches me, and every commit, merge, and push is mine.

The idea I keep coming back to: if a mistake shows up twice, it shouldn't be a model's job to catch it a third time. Write a script. That's what everything here is.

## The tools

- [attest-check](https://github.com/justin-rhee/attest-check). Checks that an AI reviewer actually named everything it approved.
- [anchor-check](https://github.com/justin-rhee/anchor-check). Catches AI-written plans that point at code that doesn't exist.
- [never-worse-backup](https://github.com/justin-rhee/never-worse-backup). A git auto-backup that stops before it can lose your work or leak a secret.
- [bash-havoc-guard](https://github.com/justin-rhee/bash-havoc-guard). A Claude Code hook that stops an agent leaking secrets or destroying files.

Each one is small, with an offline test suite, and honest about what it can't do. If a check can be fooled, I say how, right on the page.

## Tell me what I've missed

I know these aren't perfect. If you spot a gap or catch me getting something wrong, open an issue. That's usually how I learn.
