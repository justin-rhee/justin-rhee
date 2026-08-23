# Lessons

Over about eight months the same failures kept showing up, and each time one showed up twice I wrote a small check so it couldn't show up a third. Those checks are the tools on my profile. This is the other half, the part that didn't turn into code.

Most of it cost me something first. I'll keep adding as I go, and I'm sharing it in case any of it is useful in your own work:

- the second time I fix the same bug it's rent, which is how nineteen small repos happened instead of one long document about being careful
- a green result means nothing on its own, after a scan told me CLEAN while one unbalanced parenthesis made its pattern file invalid and it matched nothing at all
- guards fail open, sensors fail loud and gates fail closed, and mixing up which one I'm building is how safety tooling ends up uninstalled
- five wrong blocks nearly made me uninstall a guard I'd written two days earlier, which is why only checks that can prove their claim get to block
- escaping the characters that make an instruction parse works whether or not anything is paying attention, and telling a model to ignore that instruction does not
- a new check's first findings are usually its own, like the one that reported five healthy packages as broken and quoted its own error message as the evidence
- ten fabrications in six days out of a counterpart AI's relayed output, including one review that confidently described my project as a video-generation engine
- repo history is the part I can't take back, since commit messages and every old revision travel with the file, and a rewrite I got ninety percent right still published the other ten
- a check for how long a document should be would have landed every document just under the threshold, which is the exact sameness I was trying to prevent
- a rule with its origin incident attached survives a refactor, and one without it gets deleted by whoever can't tell what it was for, usually me, six months later

The short version: a check that reports success without having run is worse than no check at all.
