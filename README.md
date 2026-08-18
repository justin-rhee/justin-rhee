# Justin Rhee

Hi, I'm a designer building agent workflows and harnesses on OpenClaw. Every tool here exists because something broke first. These are the fixes for things I got wrong, some rebuilt more times than I'd like to admit. Sharing them in case you're hitting the same walls.

The failure that bought each tool is written at the top of its README, including the times my first fix was wrong.

## Keeping an agent inside the lines

- [bash-havoc-guard](https://github.com/justin-rhee/bash-havoc-guard). Reads every shell command your agent is about to run and stops the dangerous ones.
- [path-fence](https://github.com/justin-rhee/path-fence). Resolves a path all the way down first, then refuses the credential-shaped ones.
- [untrusted-read](https://github.com/justin-rhee/untrusted-read). Makes an agent treat a notes directory as data instead of instructions.
- [transcript-redactor](https://github.com/justin-rhee/transcript-redactor). Redacts shell output before your agent's transcript records it.

## Checking that the work actually happened

- [attest-check](https://github.com/justin-rhee/attest-check). Fails an agent's answer if anything you asked about went unmentioned.
- [anchor-check](https://github.com/justin-rhee/anchor-check). Catches plans that point at code that doesn't exist.
- [linter-selftest](https://github.com/justin-rhee/linter-selftest). A linter that proves its own rules can still fire.

## Not losing work

- [never-worse-backup](https://github.com/justin-rhee/never-worse-backup). A git auto-backup that stops before it can lose your work or push a secret.
- [cas-write](https://github.com/justin-rhee/cas-write). Compare-and-swap file writes, so a second writer can't silently erase the first.
- [guarded-deploy](https://github.com/justin-rhee/guarded-deploy). Ships only from a clean tree, on the exact commit your checks passed.

## Signals that tell the truth

- [alert-throttle](https://github.com/justin-rhee/alert-throttle). Stops a stuck check from posting the same alert forever.
- [alert-redactor](https://github.com/justin-rhee/alert-redactor). Builds alerts that carry the shape of a failure and none of its content.
- [freshness-gate](https://github.com/justin-rhee/freshness-gate). Says whether a signal is fresh, stale, or dead, from its real timestamp.

## Catching things before they ship

- [bash32-check](https://github.com/justin-rhee/bash32-check). Blocks the shell lines it can prove will kill your script partway through.
- [dash-gate](https://github.com/justin-rhee/dash-gate). Bans em and en dashes from the strings your users actually see.
- [deid-allowlist](https://github.com/justin-rhee/deid-allowlist). Drops every field you didn't explicitly allow, before a record leaves your machine.

Each one is small, tested offline, and honest about what it can't do. If a check can be fooled, its README says how.

## What building these taught me

The tools are the easy part to show. The reasoning is in [LESSONS.md](LESSONS.md): what I got wrong, what it cost, and the rules I follow now because of it. The short version: a check that reports success without having run is worse than no check at all.

## Tell me what I've missed

If you spot a gap, or catch me getting something wrong, open an issue. I'd be grateful.
