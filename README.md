# Awesome AI Slop Removal [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> Tools, rule sets, and research for detecting and removing AI slop — the words, phrases, and structural habits that make writing read as machine-made.

**AI slop** is not "text a model wrote." It is text that carries the patterns readers now associate with models: `delve`, `it's not just X, it's Y`, em dashes three to a paragraph, a closing aphorism, a `[Your Name]` placeholder nobody filled. Human writers produce it too. That is the point — it is a style problem, not an authorship problem.

This list collects what people have built to fight it, and the taxonomy of what they all detect.

- **[RULES.md](RULES.md)** — the generated rule reference: matches, editing reasons, and explicit replacement or review actions. The rule source lives in [markdownme.com](https://github.com/ravsau/markdownme.com/tree/main/scripts/enhancepost).
- **[Anti-Slop Editor](https://enhancepost.com/antislop/)** — review specific suggestions and choose each change. Draft text stays in your browser. Basic usage events exclude text.

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
- [Related lists](#related-lists)
- [Contributing and feedback](#contributing-and-feedback)

## Why a list

The rule sets below were written independently and converge hard. Six of them
found the em dash first. Five found `it's not just X, it's Y`. That convergence is
the useful signal, and it is scattered across a dozen `SKILL.md` files.

The three things this list adds:

1. **One taxonomy** ([RULES.md](RULES.md)) instead of a dozen overlapping ones.
2. **Category labels** so you can tell an agent skill from a linter from a detector before you install anything.
3. **A false-positive channel.** Every rule here fires on genuine human writing sometimes. [Report one](https://github.com/ravsau/awesome-ai-slop-removal/issues/new?template=false-positive.yml) and it gets fixed in the taxonomy.

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
> A pattern match does not establish who wrote a text. Placeholders, citation
> tokens, and tracking links need context too. Use the rules to review writing,
> not to accuse a student or colleague of using AI.

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
| [Anti-Slop Editor](https://enhancepost.com/antislop/) | Highlights writing patterns for review. Offers explicit replacements where available and leaves other edits to you. Draft text stays in your browser. |
| [The AI slop words and phrases list](https://enhancepost.com/blog/ai-slop-words-phrases-list/) | The public rule reference, generated from the same source as the editor and RULES.md. |

<sub>EnhancePost is maintained by this list's author. Everything else is third-party.</sub>

## The taxonomy

See **[RULES.md](RULES.md)** for the current categories, examples, and editing actions.
That file and the EnhancePost reference article are generated from one structured
[source](https://github.com/ravsau/markdownme.com/blob/main/scripts/enhancepost/rules.json).

Formatting findings identify things such as placeholders and unusual characters.
Style suggestions identify wording to review. Neither category proves authorship.
A phrase can be appropriate in context, so keeping it is a valid decision.

## Related lists

Three neighbours, none of which this list duplicates. Check them — one may fit you better.

| List | ★ | What it does differently |
|---|--:|---|
| [hwajongpark/awesome-slop](https://github.com/hwajongpark/awesome-slop) | 5 | Organized **by language**: Korean 번역투, Russian канцелярит, Chinese 公文腔, Vietnamese Hán-Việt. Go here if you publish outside English — it is deeper on that than the [Non-English](#non-english) section below. |
| [discountry/awesome-anti-ai-slop](https://github.com/discountry/awesome-anti-ai-slop) | 12 | A tools collection with a Chinese README. One commit, last touched 2026-05-27. |
| [yikerman/awesome-ai-slop](https://github.com/yikerman/awesome-ai-slop) | 25 | The opposite list: a curated collection **of** AI slop projects, as mockery. Named almost identically to this one — if you were looking for that, it is there. |

The rule reference explains the patterns used by the EnhancePost editor. The
project tables above help you compare other implementations and their approaches.

## Contributing and feedback

Four issue forms, so nothing needs a pull request unless you want to write one:

- **[Add a project](https://github.com/ravsau/awesome-ai-slop-removal/issues/new?template=add-project.yml)** — anything missing from the tables above.
- **[Add or correct a rule](https://github.com/ravsau/awesome-ai-slop-removal/issues/new?template=add-rule.yml)** — a tell RULES.md does not cover, or a replacement that is wrong.
- **[Report a false positive](https://github.com/ravsau/awesome-ai-slop-removal/issues/new?template=false-positive.yml)** — a rule that fired on writing that was fine. **The most useful report you can file.** Every rule here over-fires somewhere, and the only way to find out is for someone to hit it.
- **[Tool feedback](https://github.com/ravsau/awesome-ai-slop-removal/issues/new?template=tool-feedback.yml)** — a suggestion was unclear, the tool broke, or an edit damaged the meaning.

When reporting a false positive, include the stable rule ID from [RULES.md](RULES.md) and a short, non-confidential example.

See [CONTRIBUTING.md](CONTRIBUTING.md) for what gets accepted. Short version: a
project needs a public rule set or working code. A rule needs an editing reason
and a safe replacement or clear manual-review guidance.

## License

[CC0-1.0](LICENSE). The list is public domain. Linked projects keep their own licenses.
