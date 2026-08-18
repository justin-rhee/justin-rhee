# Lessons

A running list I keep for myself while building agent workflows. It grows whenever something breaks in a way I didn't see coming, which is more often than I'd like.

Over about eight months the same failures kept showing up, and each time one showed up twice I wrote a small check so it couldn't show up a third. Those checks are the tools on my profile. This is the other half, the part that didn't turn into code.

Most of it cost me something first.

## Pay for a bug twice and you should have written a script

The first time something breaks you fix it. The second time it's rent. Sixteen small repos instead of one long document about being careful.

## Absence must never read as a pass

This is the one I keep relearning, and it's why a green result on its own stopped meaning anything to me.

A scan told me CLEAN while matching nothing at all, because one unbalanced parenthesis in a comment line made its pattern file invalid and the tool just kept going. A linter reported a clean corpus three times while one of its rules had never once executed. A test suite passed against a directory that didn't exist. A CI job went green having found no tests to run.

Every one of those printed exactly what you see when things are genuinely fine.

So now: a missing input is a failure, not a pass. No config means exit non-zero. An empty diff means refuse. A dependency that can't be found means UNKNOWN, and UNKNOWN is a failure state, not a shrug. If a check can't tell you it ran, it didn't. [linter-selftest](https://github.com/justin-rhee/linter-selftest) exists entirely because of this one, and [attest-check](https://github.com/justin-rhee/attest-check) is the same idea pointed at an agent's answer.

## Guards fail open, sensors fail loud, gates fail closed

These three want opposite things, and mixing them up is how safety tooling ends up uninstalled.

A guard sits in front of something you do all day. If it breaks it has to allow, or you'll rip it out the first afternoon it blocks your own work. A sensor exists to tell you something, so if it breaks it has to say so instead of reporting all-clear. A gate stands in front of something irreversible, so if it breaks it has to refuse.

Each of my tools sits in exactly one of those roles, and its README says which. [bash-havoc-guard](https://github.com/justin-rhee/bash-havoc-guard) fails open on purpose, [guarded-deploy](https://github.com/justin-rhee/guarded-deploy) fails closed on purpose, and [freshness-gate](https://github.com/justin-rhee/freshness-gate) is a sensor that refuses to call an unknown thing fine.

## Five wrong blocks nearly cost me a tool I wrote myself

I was ready to uninstall it. I'd written it two days earlier.

A guard strict enough to matter and quiet enough to keep is a genuinely hard line to find, and it isn't a technical problem. Once you're in the habit of waiving findings you waive the real ones the same way, without reading them. So anything that fires on a guess gets demoted to a warning, and only checks that can prove their claim get to block. [bash32-check](https://github.com/justin-rhee/bash32-check) splits its findings that way for exactly this reason.

## Make it impossible before you make it noticed

Telling a model to ignore instructions inside a file is a behavioral defense. It works until it doesn't. Escaping the characters that make those instructions parse at all is structural, and it works whether or not anything is paying attention.

Where I had the choice I took the dumb deterministic version. The clever one fails in ways you find out about later. [untrusted-read](https://github.com/justin-rhee/untrusted-read) is the clearest case: it escapes characters rather than asking a model to notice anything.

## New checks mostly find themselves at first

I keep expecting a fresh check to find bugs. Usually its first several findings are its own.

A checker I built to verify install instructions reported five healthy packages as broken, quoting its own error message as the evidence. A guard meant to catch one bad pattern in my writing fired on four clean turns in a row, citing lines from a message that no longer existed. A detector built to find a specific defect turned out to be blind to the most common way that defect gets written, which I only learned because I wrote a control fixture to prove it worked.

So a new instrument gets pointed at a known-good case and a known-bad case before any of its numbers are allowed to mean anything. Confidence is not the gate. Where the expected value came from is.

## Ten fabrications in six days

That's what I logged from a counterpart AI's relayed output: invented mechanisms, filenames that didn't exist, statistics from nowhere. One external review confidently described my project as a video-generation engine.

None of it was malice. It's what fluent generation looks like when nothing checks it. So a claim about what a tool does gets verified by running the tool, and that goes double when the summary agrees with what I already believed.

## Repo history is the part you can't take back

Scrubbing a file is easy. Scrubbing a repository isn't, because commit messages, author identity and every old revision travel with it, and a rewrite you got ninety percent right still published the other ten.

Every package here starts from an empty directory and a fresh first commit. It costs a few minutes and removes a whole category of mistake you can't undo.

## Some rules get worse when you enforce them

I started writing a check for how long a document should be. Then I worked out what it would actually do: every document would land just under the threshold, and sixteen packages would converge on one shape, which is the exact sameness I was trying to prevent.

A gate catches structure fine. Does this section exist, does this test run, does this history say the right thing. It can't catch rhythm and it can't catch judgment, and pretending otherwise just manufactures uniformity and calls it quality.

## Write down the failure that bought the rule

Every tool here has its origin incident at the top of its README, including the times my first fix was wrong. A rule with a story attached survives a refactor. A rule without one gets deleted by someone who couldn't tell what it was for, which is usually me, six months later.
