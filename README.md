# Justin Rhee

Hi, I'm Justin, a product designer building with AI agents. I'm exploring how evaluations can help improve agent harnesses and sharing what I learn along the way, in case it helps someone else:

<!-- tools:start -->

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
- [model-gate](https://github.com/justin-rhee/model-gate): holds your model API key so the agent never does, opens only during a session, and caps its tokens

## Many agents, one codebase

- [never-worse-backup](https://github.com/justin-rhee/never-worse-backup): keeps an auto-backup from saving another session's half-finished work
- [cas-write](https://github.com/justin-rhee/cas-write): stops one writer from silently erasing another's changes
- [take-once](https://github.com/justin-rhee/take-once): lets several coding agents share one task list without two of them grabbing the same task

<!-- tools:end -->

## Tenets I keep coming back to

1. Don't trust checks you haven't seen fail
2. Write the prediction down before the agents start
3. Don't let agents grade their own work
4. Expect agents to optimize the number, not necessarily the outcome
5. Block on proof, warn on the rest
6. Put guardrails in the structure, not the prompt
7. Cut high-entropy code, even when it works
8. Make the second failure the last
