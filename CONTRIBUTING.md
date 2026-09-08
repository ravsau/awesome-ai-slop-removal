# Contributing

Use an [issue form](https://github.com/ravsau/awesome-ai-slop-removal/issues/new/choose).
Nothing here needs a pull request unless you want to write one.

## The bar for a project

A project gets listed if it has a **public rule set or working code**. A landing
page with a waitlist does not qualify, however good the idea is. The value of
this list is that you can read what a tool actually checks before you install it.

Not listed, deliberately:

- **Paid black-box "AI detectors"** that sell an authorship verdict. They cannot
  prove authorship, they are wrong often enough to ruin someone's week, and
  linking them here would lend them a credibility they have not earned.
- **"Humanizers" that sell detector evasion** as the product. Same rules, worse intent.

Self-promotion is fine. Say it is yours in the issue. Two entries on this list
are mine and are labelled as such.

## The bar for a rule

A rule needs three things:

1. **The tell.** The word, phrase, or pattern.
2. **An editing reason and action.** Give a safe replacement or clear manual-review
   guidance. Do not make deletion the default for words that carry meaning.
3. **When a human writes it legitimately.** Every rule over-fires somewhere.
   Include a legitimate example alongside the example that needs editing.

## False positives are the most valuable report

They are also the hardest to get, because the person who hits one is annoyed and
closes the tab. If you file one you are doing the single most useful thing
available: [the form](https://github.com/ravsau/awesome-ai-slop-removal/issues/new?template=false-positive.yml)
takes a minute.

## Style

- Plain English. This is a list about not writing like a machine.
- One line per entry. Say what the project contributes that the others do not.
- No superlatives. "The best" and "revolutionary" are on the list of tells in RULES.md.

## Data freshness

Star counts and licenses come from the GitHub API and are dated in README.md.
They go stale. If one is badly out of date, say so in an issue.

## Updating the generated reference

Do not edit RULES.md by hand. Update the structured catalog in
[markdownme.com/scripts/enhancepost/rules.json](https://github.com/ravsau/markdownme.com/blob/main/scripts/enhancepost/rules.json).
The generator produces the editor data, public article tables, and RULES.md.
From that checkout, export a reviewed copy to this checkout:

```sh
python3 scripts/enhancepost/build_rules.py --docs-dest ../awesome-ai-slop-removal/RULES.md
```

Run the EnhancePost checks before submitting a rule change. A regex match identifies
a pattern, not authorship. Include a test for a legitimate use when changing a rule.
