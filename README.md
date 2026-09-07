# Awesome AI Slop [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> Tools, rule sets, and research for detecting and removing AI slop — the words, phrases, and structural habits that make writing read as machine-made.

**AI slop** is not "text a model wrote." It is text that carries the patterns readers now associate with models: `delve`, `it's not just X, it's Y`, em dashes three to a paragraph, a closing aphorism, a `[Your Name]` placeholder nobody filled. Human writers produce it too. That is the point — it is a style problem, not an authorship problem.

This list collects what people have built to fight it, and the taxonomy of what they all detect.

- **[RULES.md](RULES.md)** — the tell taxonomy: 13 categories, 200+ tells, each with a plain replacement. Compiled from the rule files of every project below.
- **[Slop Score](https://enhancepost.com/slopscore/)** — paste text, get a 0–100 density score against those rules. Runs in your browser, uploads nothing.

## Contents

- [Why a list](#why-a-list)
- [Rule sets and agent skills](#rule-sets-and-agent-skills)
- [Deterministic linters](#deterministic-linters)
- [System prompts](#system-prompts)
- [Detectors](#detectors)
- [Design and UI slop](#design-and-ui-slop)
- [Code slop](#code-slop)
- [Non-English](#non-english)
- [Web tools](#web-tools)
- [The taxonomy](#the-taxonomy)
- [Contributing and feedback](#contributing-and-feedback)

## Why a list

The rule sets below were written independently and converge hard. Six of them
found the em dash first. Five found `it's not just X, it's Y`. That convergence is
the useful signal, and it is scattered across a dozen `SKILL.md` files.

The three things this list adds:

1. **One taxonomy** ([RULES.md](RULES.md)) instead of a dozen overlapping ones.
2. **Category labels** so you can tell an agent skill from a linter from a detector before you install anything.
3. **A false-positive channel.** Every rule here fires on genuine human writing sometimes. [Report one](https://github.com/ravsau/awesome-ai-slop/issues/new?template=false-positive.yml) and it gets fixed in the taxonomy.

Star counts and licenses are from the GitHub API, checked 2026-09-07.

## Rule sets and agent skills

Install into Claude Code, Codex, Cursor, or ChatGPT. They edit a draft on request.

| Project | ★ | License | What it contributes |
|---|--:|---|---|
| [blader/humanizer](https://github.com/blader/humanizer) | 44.9k | MIT | The largest single rule set. Vocabulary plus cadence rules. |
| [hardikpandya/stop-slop](https://github.com/hardikpandya/stop-slop) | 16.9k | MIT | Business jargon, false agency, structural clichés. |
| [petergyang/no-ai-slop](https://github.com/petergyang/no-ai-slop) | 7.5k | MIT | 20+ patterns: weasel attribution, colon reveals, faux-insight setups, synonym cycling, fake-profound endings. Has a detect-only mode. |
| [harshaneel/humanize](https://github.com/harshaneel/humanize) | 425 | MIT | Nine levers with a benchmark harness in CI. |
| [Anbeeld/WRITING.md](https://github.com/Anbeeld/WRITING.md) | 366 | MIT | A formula watchlist, and the only project that documents *editing distortions* — the ways a de-slop pass silently changes your meaning. |
| [NulightJens/humanizer-stack](https://github.com/NulightJens/humanizer-stack) | 260 | — | Splits the work into a surface pass and a structural pass. Copy tells ranked by cite-share from a 3.2M-post Reddit study. |
| [seyedehsanhadi/sloptrim](https://github.com/seyedehsanhadi/sloptrim) | 209 | Apache-2.0 | A 71-pattern catalogue with before/after pairs for every rule. The most complete taxonomy published. Includes machine artifacts nobody else covers. |

## Deterministic linters

No model in the loop. Fixed rules, repeatable output, cheap enough for CI.

| Project | ★ | License | What it contributes |
|---|--:|---|---|
| [berelevant-ai/slopless](https://github.com/berelevant-ai/slopless) | 324 | MIT | textlint rules and a CLI for English Markdown. |
| [eric-tramel/slop-guard](https://github.com/eric-tramel/slop-guard) | 163 | MIT | 25 scored rules — em-dash density, colon density, bullet density, closing aphorism, paragraph balance — fitted against a public-domain newspaper corpus. |
| [seyedehsanhadi/sloptrim](https://github.com/seyedehsanhadi/sloptrim) | 209 | Apache-2.0 | Python standard library only. No network, no model. Also listed above. |

## System prompts

Cheaper than editing: stop the slop at generation time.

| Project | ★ | License | What it contributes |
|---|--:|---|---|
| [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill) | 85.1k | MIT | The largest of these by far. Aims at generic output broadly, not prose tells alone. |
| [hexiecs/talk-normal](https://github.com/hexiecs/talk-normal) | 1.8k | MIT | One hard constraint against negation-framed claims, in any language or position. Publishes its reduction benchmarks per model. |
| [alexgreensh/attention-span](https://github.com/alexgreensh/attention-span) | 1.0k | AGPL-3.0 | Output styles that cut agent verbosity. |

## Detectors

Score or classify text rather than rewrite it.

| Project | ★ | License | What it contributes |
|---|--:|---|---|
| [distil-labs/distil-ai-slop-detector](https://github.com/distil-labs/distil-ai-slop-detector) | 93 | Apache-2.0 | Runs locally in the browser. Nothing uploaded. |
| [SicariusSicariiStuff/SLOP_Detector](https://github.com/SicariusSicariiStuff/SLOP_Detector) | 101 | Apache-2.0 | Dictionary-based scoring for shareGPT JSON and plain text. Useful for filtering training data. |
| [gouwsxander/slop-detector](https://github.com/gouwsxander/slop-detector) | 61 | MIT | An end-to-end detector build, written up as a walkthrough. |
| [ctkrug/tellsign](https://github.com/ctkrug/tellsign) | 0 | MIT | In-browser highlighter with weighted word and phrase tells. Deliberately a style checker, not a black-box authorship verdict. |

> [!WARNING]
> No detector can prove authorship. They measure style, and they are wrong often
> enough that using one to accuse a student or a colleague is indefensible. The
> one exception is the machine-artifact category in [RULES.md](RULES.md) — leaked
> citation tokens and unfilled placeholders have no human cause.

## Design and UI slop

The visual equivalent: purple gradients, the same hero, the same card grid.

| Project | ★ | License | What it contributes |
|---|--:|---|---|
| [Nutlope/hallmark](https://github.com/Nutlope/hallmark) | 28.2k | MIT | Anti-slop design skill for Claude Code, Cursor, and Codex. |
| [Trystan-SA/claude-design-system-prompt](https://github.com/Trystan-SA/claude-design-system-prompt) | 1.9k | MIT | Reverse-engineered design system prompt, accessibility-aware. |
| [miqdadbadjuber/anti-slop](https://github.com/miqdadbadjuber/anti-slop) | 1.6k | MIT | Agent rules covering generic UI, text, and code together. |
| [yetone/kill-ai-slop](https://github.com/yetone/kill-ai-slop) | 1.1k | Apache-2.0 | A field guide to the visual and copy tics of AI-generated products, plus a skill that strips them. |
| [Gesso-Build/skills](https://github.com/Gesso-Build/skills) | 84 | MIT | 73 deterministic design guards for HTML and CSS. |

## Code slop

Dead code, swallowed errors, fake docstrings, over-engineering.

| Project | ★ | License | What it contributes |
|---|--:|---|---|
| [dmmulroy/anti-slop](https://github.com/dmmulroy/anti-slop) | 4.2k | MIT | Oxlint rules rejecting low-evidence TypeScript and JavaScript patterns. |
| [scanaislop/aislop](https://github.com/scanaislop/aislop) | 599 | MIT | Dead code, unsafe casts, swallowed errors, duplication. |
| [rsionnach/sloppylint](https://github.com/rsionnach/sloppylint) | 89 | — | Python: over-engineering, hallucinated APIs, dead code. |
| [flamehaven01/AI-SLOP-Detector](https://github.com/flamehaven01/AI-SLOP-Detector) | 85 | MIT | Empty functions, fake documentation, inflated comments. |

## Non-English

Slop is language-specific. A rule set trained on English tells misses these.

| Project | ★ | License | Language |
|---|--:|---|---|
| [epoko77-ai/im-not-ai](https://github.com/epoko77-ai/im-not-ai) | 5.3k | MIT | Korean — translationese, mechanical parallelism, 71 tells |
| [MrGeDiao/shuorenhua](https://github.com/MrGeDiao/shuorenhua) | 1.5k | MIT | Chinese — 说人话, fact-preserving rewrite |
| [hexiecs/talk-normal](https://github.com/hexiecs/talk-normal) | 1.8k | MIT | English and Chinese negation frames |

## Web tools

No install.

| Tool | What it does |
|---|---|
| [Slop Score](https://enhancepost.com/slopscore/) | Paste text, get a 0–100 density score and a per-category breakdown against [RULES.md](RULES.md). Client-side, nothing uploaded, no signup. |
| [EnhancePost](https://enhancepost.com/) | Rewrites what the score finds. Underlines each hit with a one-click plain replacement, and de-slops without inventing facts. |
| [The AI slop words and phrases list](https://enhancepost.com/blog/ai-slop-words-phrases-list/) | The long-form version of RULES.md, with a replacement for every entry. |

<sub>Slop Score and EnhancePost are maintained by this list's author. Everything else is third-party.</sub>

## The taxonomy

The short version. Full detail, with replacements, in **[RULES.md](RULES.md)**.

| # | Category | Example | Precision |
|---|---|---|---|
| 1 | Machine artifacts | `[Your Name]`, `utm_source=chatgpt.com`, zero-width chars | **Certain** |
| 2 | Marketing templates | "unlock the full potential", "stay ahead of the curve" | Very high |
| 3 | Sentence patterns | superficial `-ing` tails, weasel attribution | High |
| 4 | Structural patterns | em dashes, negation frames, closing aphorisms | High |
| 5 | Tell-phrases | "in today's fast-paced world", "let's dive in" | High |
| 6 | Brochure register | nestled, picturesque, world-class | Medium |
| 7 | Tell-words | delve, leverage, tapestry, holistic | Low alone |
| 8 | Business jargon | circle back, move the needle, bandwidth | Low alone |
| 9 | Transition crutches | moreover, furthermore, notably | Low alone |
| 10 | Hyphenated clichés | mission-critical, battle-tested, plug-and-play | Low alone |
| 11 | Filler grammar | "make a decision on" → "decides" | Low alone |
| 12 | Model dialects | Claude: genuinely, nuanced · GPT: supercharge, skyrocket | Context only |
| 13 | Rhythm and cadence | uniform sentence and paragraph length | Human eye only |

**Density is the signal, not the word.** Every entry in categories 6–11 appears in
good human writing. One is a coincidence. Five in a paragraph is a fingerprint.
Category 1 is the exception: those have no human cause, so one is enough.

## Contributing and feedback

Four issue forms, so nothing needs a pull request unless you want to write one:

- **[Add a project](https://github.com/ravsau/awesome-ai-slop/issues/new?template=add-project.yml)** — anything missing from the tables above.
- **[Add or correct a rule](https://github.com/ravsau/awesome-ai-slop/issues/new?template=add-rule.yml)** — a tell RULES.md does not cover, or a replacement that is wrong.
- **[Report a false positive](https://github.com/ravsau/awesome-ai-slop/issues/new?template=false-positive.yml)** — a rule that fired on writing that was fine. **The most useful report you can file.** Every rule here over-fires somewhere, and the only way to find out is for someone to hit it.
- **[Tool feedback](https://github.com/ravsau/awesome-ai-slop/issues/new?template=tool-feedback.yml)** — the score felt wrong, the tool broke, an output was bad.

You can also send a false positive straight from [Slop Score](https://enhancepost.com/slopscore/#fb) without a GitHub account. Those land in the same triage.

See [CONTRIBUTING.md](CONTRIBUTING.md) for what gets accepted. Short version: a
project needs a public rule set or working code, and a rule needs a plain-English
replacement — a ban list with no replacement is half a rule.

## License

[CC0-1.0](LICENSE). The list is public domain. Linked projects keep their own licenses.
