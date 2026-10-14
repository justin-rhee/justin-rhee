# Justin Rhee

Hi, I'm Justin, a product designer exploring evaluation-driven development to improve harnesses and build agent teams. I share what I've learned the hard way, in case it helps anyone else building with agents:

## Evidence over claims

- [attest-check](https://github.com/justin-rhee/attest-check): rejects a reply that leaves out anything you asked about
- [anchor-check](https://github.com/justin-rhee/anchor-check): catches plans that cite files that don't exist
- [judgment-check](https://github.com/justin-rhee/judgment-check): has agents commit to a prediction first, then a different agent scores it
- [scar-audit](https://github.com/justin-rhee/scar-audit): shows which written rules your agent quietly skips
- [hook-canary](https://github.com/justin-rhee/hook-canary): proves an installed hook still works by running it

## Boundaries that hold

- [bash-havoc-guard](https://github.com/justin-rhee/bash-havoc-guard): blocks credential dumps, outbound network calls and destructive commands
- [untrusted-read](https://github.com/justin-rhee/untrusted-read): stops instructions hidden in shared notes from steering an agent
- [transcript-redactor](https://github.com/justin-rhee/transcript-redactor): keeps credentials out of agent transcripts
- [touchset-gate](https://github.com/justin-rhee/touchset-gate): flags any file an agent changed outside its task

## Many agents, one codebase

- [never-worse-backup](https://github.com/justin-rhee/never-worse-backup): keeps an auto-backup from saving another session's half-finished work
- [cas-write](https://github.com/justin-rhee/cas-write): stops one writer from silently erasing another's changes

## Tenets I keep coming back to

1. Trust no check you haven't seen fail
2. Write the prediction down before the agents start
3. Never let the work grade itself
4. Expect agents to optimize the number, not necessarily the outcome
5. Block on proof, warn on the rest
6. Put guardrails in the structure, not the prompt
7. Cut high-entropy code, even when it works
8. Make the second failure the last
