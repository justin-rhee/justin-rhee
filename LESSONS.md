# What building these taught me

I build agent workflows for my own work. Over about eight months the same kinds
of failure kept arriving, and each time one arrived twice I wrote a small
deterministic check so it couldn't arrive a third time. Those checks are the
tools on my profile. These are the things I learned that are not code.

Most of them cost me something before I understood them.

## A defect class paid for twice becomes a script

The first time something breaks, you fix it. The second time the same shape
breaks, you're paying rent. Every class caught deterministically compounds,
because the check keeps working while you sleep; every class re-found by hand,
or by a model reading a diff, gets re-found forever at full price.

That's the whole reason there are sixteen small repos instead of one long
document about being careful.

## Absence must never read as a pass

This is the one I've learned the most times, and it's the reason I no longer
trust a green result on its own.

A scan reported CLEAN while matching nothing at all, because one unbalanced
parenthesis in a comment line made its pattern file invalid and the tool kept
going. A test suite reported success on a corpus it never read, because a
mistyped path resolved to an empty directory. A linter reported a clean corpus
three times while one of its rules had never once executed. In every case the
output was identical to the output you get when everything is genuinely fine.

So: a missing input is a failure, not a pass. No allowlist means exit non-zero,
not exit zero. An empty diff means refuse, not approve. A dependency that can't
be found means UNKNOWN, and UNKNOWN is a failure state.

## Guards fail open, sensors fail loud, gates fail closed

These three want opposite things and getting them mixed up is how safety tooling
gets deleted.

A guard sits in front of something you do constantly, so if it breaks it must
allow, or you will remove it the first afternoon it blocks your own work. A
sensor exists to tell you something, so if it breaks it must say so rather than
report all-clear. A gate stands in front of an irreversible act, so if it breaks
it must refuse.

Every one of my tools sits in exactly one of those three roles, and each README
says which, because the failure behavior is the most important thing about it.

## The false-positive economy is real

Five wrong blocks in one night nearly cost a guard its legitimacy. I was ready to
uninstall my own tool, and I wrote it.

A guard strict enough to matter and quiet enough to keep is a genuinely hard
balance, and it isn't a technical problem. Once someone is in the habit of
waiving findings, they waive the real ones the same way, without reading them. So
a check that fires on a guess gets demoted to a warning, and only checks that can
prove their claim are allowed to block.

## Structural beats behavioral

If you can make a bad thing impossible to express, do that instead of asking
something to notice it.

A model told not to follow instructions in a file is a behavioral defense: it
works until the day it doesn't. Escaping the characters that make those
instructions parse at all is structural, and it works whether or not anything is
paying attention. Where I had a choice, I took the dumb deterministic version,
because the clever version fails in ways you find out about later.

## Verify relayed output against ground truth

Over six days I logged ten separate cases of a counterpart AI's relayed output
failing verification: invented mechanisms, imagined filenames, statistics that
came from nowhere. One external review confidently described my project as a
video-generation engine.

None of that was malice and none of it was even unusual. It's what fluent
generation looks like when nothing checks it. So a claim about a tool's behavior
gets verified by running the tool, not by reading a summary of it, and that
applies most strongly when the summary agrees with what I already believed.

## The instrument is the first thing to doubt

When I write a new check, its early findings are usually about itself.

A checker built to verify install instructions reported five healthy packages as
broken, using text from its own error message as the evidence. A guard designed
to catch one bad pattern in my writing fired on four consecutive clean turns,
citing lines from a message that no longer existed. A detector meant to find a
specific defect couldn't see the most common way that defect is written, which I
learned only because I wrote a control fixture to prove it worked.

So a new instrument gets pointed at a known-good case and a known-bad case before
any of its numbers are allowed to mean anything.

## Repo history is the irreversible part

Scrubbing a file is easy. Scrubbing a repository isn't, because commit messages,
author identity, and every previous revision travel with it, and a rewrite you
got ninety percent right still published the other ten.

Every one of these packages starts from an empty directory and a fresh first
commit. Nothing is carried over from where the code originally lived. It costs a
few minutes and removes an entire category of mistake that can't be undone.

## Some standards cannot be enforced without ruining them

I tried to write a check for how long a document should be. Then I realized what
it would actually do: every document would land just under the threshold, and
sixteen packages would converge on the same shape, which is the exact sameness
the rule was meant to prevent.

Mechanism doesn't fit every rule. A gate catches structure well: does this
section exist, does this test run, does this history say the right thing. It
can't catch rhythm, and it can't catch judgment. Trying anyway produces
uniformity and calls it quality.

## Write the failure at the top of the file

Every tool here has its origin incident in a comment or a README, including the
wrong diagnoses along the way.

Partly that's honesty. Mostly it's that the next person to read the code, which
is usually me six months later, needs to know which line is load-bearing and
which is decoration. A rule with a story attached survives a refactor. A rule
without one gets deleted by someone who couldn't tell what it was for.
