# The AI slop tell taxonomy

13 categories, 200+ tells, each with a plain replacement. Compiled from the rule
files of every project in [README.md](README.md), checked 2026-09-07.

**Read this first.** Every entry in categories 6 through 11 appears in good human
writing. One hit is a coincidence. Five in a paragraph is a fingerprint. Score
**density**, never single words — that is the difference between an editing tool
and a witch hunt. Category 1 is the only exception.

Paste a draft into [Slop Score](https://enhancepost.com/slopscore/) to run all of
this automatically in your browser.

---

## 1. Machine artifacts — precision: certain

These have no human cause. A writer has no reason to produce them, so one hit is
enough. Check for these first: it is the fastest pass and the only certain one.

| Tell | Example | Fix |
|---|---|---|
| Unfilled placeholder | `[Your Name]`, `[INSERT URL]`, `[COMPANY]`, `[DATE]`, `lorem ipsum` | Fill with the real value. **Never invent one** — the tell was the unfinished template, and a fabricated name is worse. |
| Leaked citation token | `citeturn0search0`, `oai_citation`, `contentReference`, `【12†source】` | Delete. Leave the claim as it was. Do not invent a source to fill the gap. |
| Chat tracking parameter | `?utm_source=chatgpt.com`, `perplexity.ai`, `claude.ai`, `gemini.google.com` | Strip everything from the `?` onward. |
| Zero-width / control chars | U+200B, U+200D, U+FEFF, U+00AD, bidi U+202A–U+202E | Invisible on screen, visible to every detector. Retype or paste as plain text. |
| Non-standard spaces | U+00A0, U+202F, U+2000–U+200A, U+3000 | Look like spaces, are not. Normalize to U+0020. |
| Homoglyphs | Cyrillic `а`/`о` inside `pаssword`, `wrоng` | Usually a paraphrasing tool evading a detector. Retype the word. |
| Assistant register | "As an AI language model", "as of my last knowledge update", "Great question!" | Delete the sentence. |

## 2. Marketing templates — precision: very high

Full templates, not single words. A human editor almost always cuts these, so
they survive mainly in unedited output.

| Template | Fix |
|---|---|
| Unlock the full potential of… | Say what the reader gets, and how |
| Navigate the complexities of… | Name the complication, then the handling |
| A testament to the power of… | Give the result that proves it |
| Stay ahead of the curve | Name what changed and what to do |
| Turn challenges into opportunities | Name the challenge and the response |
| Working smarter, not harder | Name the step you removed |
| Drive meaningful impact | Give the metric that moved |
| Seamlessly integrate with… | Name the integration and the setup time |
| Something for everyone | Delete. Nothing is for everyone. |
| More important than ever | Say why now, with a date |
| Empowering teams to… | Say what teams can now do that they couldn't |
| Revolutionizing the way we… | Describe the old way and the new way |
| Your workflow, reimagined | Say what changed in the workflow |
| The future is full of possibilities | Delete |

## 3. Sentence patterns — precision: high

- **Weasel attribution.** "Experts agree", "studies show", "research suggests", "critics note" — with no source. Name the source or cut the claim.
- **Superficial `-ing` tails.** `, highlighting / reflecting / symbolizing / underscoring / showcasing / signaling / demonstrating / embodying`. Significance instead of fact. Replace the tail with a second fact. Note: `, resulting in` and `, enabling` are fine — those are real outcomes.
- **Outcome speculation tails.** `, raising questions about`, `, sparking debate`, `, with broader implications for`, `, paving the way for`. Cut the tail, add a checkable sentence.
- **False ranges.** "from strategy to execution", "from startups to global enterprises". The ends are not on a real scale. List the actual items.
- **Synonym cycling.** "The company… the firm… the organization… the business", all one referent. Pick one name and keep it. Humans just say "it".
- **Stacked adjective chains.** Four or more before a noun: "a bold, ambitious, transformative, forward-thinking initiative". Cut them all and describe the thing.
- **"Simple yet X."** simple yet powerful / effective / elegant. Say what is simple and what it does.
- **Question-answer drama.** "Is it perfect? No. Will it scale? Absolutely." Write one plain sentence.
- **Hedge stacking.** "may potentially suggest it could, in some cases, be somewhat effective." Keep at most one hedge.
- **Self-thoroughness.** "this comprehensive guide", "everything you need to know". Never advertise your own coverage.
- **Faux-insight setups.** "what nobody tells you", "the part everyone misses". Cut the setup, state the claim.
- **False agency.** "the decision emerges", "the culture shifts", "the data tells us". Name who did it.
- **Lazy extremes.** every, always, never, everyone, nobody. Give the number or the case.
- **No contractions.** Machine-formal register. Read it aloud and write what you said.

## 4. Structural patterns — precision: high

They survive every word swap, which is why word-level fixes alone never work.

- **Em dashes**, several per paragraph. The single most-cited tell across every project here. Use a comma or a period. **Do not substitute a colon** — readers flag that as the same reflex in a different hat.
- **Negation frames.** "It's not just a product, it's a movement." / "The question isn't X, it's Y." / "Not because X. Because Y." State the positive claim alone.
- **Tailing negations.** "no fluff, just results", "no wasted motion". Replace with the positive consequence.
- **Negative listing.** "Not a tool. Not a template. A system." State the answer.
- **The rule of three.** Forced triplets where you had two real points. Only a tell when all three are single-word generic descriptors — "composite blades, turbine housings, and structural panels" is a normal list.
- **Dramatic fragmentation.** "That's it. That's the whole thing."
- **Rhetorical-question openers.** "Ever wondered why…?", "What if I told you…"
- **Meandering intro.** Definitions, history, and why-this-matters for three paragraphs before the first fact. Delete everything above your first real claim.
- **Fake-profound kickers.** "The future isn't coming. It's already here." Delete and end on the last concrete point.
- **Summary-recap endings.** "In conclusion", "in summary", "the key takeaway is". The reader was just there.
- **Conditional next-step menus.** "If you want, I can also…" Name the action or take it.
- **Bold-term bullet runs.** Every bullet as **term**: definition. One list is fine; three is a template.
- **Decorative horizontal rules.** Three or more `---` as furniture. Human markdown uses one, or none.
- **Formatting slop.** Emoji in headings, Title Case On Everything, random mid-sentence bold, bullets where prose reads better.
- **Padding and restatement.** Cutting a third of an AI draft usually improves it.

## 5. Tell-phrases — precision: high

Openers: `thrilled to announce`, `excited to share`, `humbled and honored`,
`in today's fast-paced world`, `in the ever-evolving landscape of`,
`in a world where`, `in an era of`, `more than ever before`, `picture this`,
`imagine a world where`, `let's dive in`, `let's delve into`, `let's explore`.

Hedges and pivots: `it's important to note`, `it's worth noting`,
`it bears mentioning`, `one thing to consider is`, `a key consideration is`,
`it cannot be overstated that`, `it should be noted that`.

Authority tropes: `here's the thing`, `make no mistake`, `the truth is`,
`let's be honest`, `at its core`, `fundamentally`, `the real question is`,
`the heart of the matter`, `at the end of the day`, `in reality`,
`the bottom line is`, `when you get down to it`.

Closers: `let that sink in`, `read that again`, `the future is bright`,
`let's build it together`, `agree?`, `thoughts?`, `feel free to reach out`,
`hope this helps`.

Most of these are **deletable outright**. If the sentence still reads without the
phrase, the phrase was slop. Do not rewrite them.

## 6. Brochure register — precision: medium

`nestled`, `in the heart of`, `picturesque`, `charming`, `idyllic`, `quaint`,
`breathtaking`, `stunning`, `must-visit`, `renowned`, `acclaimed`, `celebrated`,
`world-class`, `best-in-class`, `top-tier`, `premier`, `leading`,
`industry-leading`, `state-of-the-art`, `rich` (figurative).

Every one praises without observing. Replace with the thing you actually saw.

## 7. Tell-words — precision: low alone

**Verbs and adjectives:** delve, leverage, unlock, unleash, unveil, elevate,
empower, foster, harness, streamline, supercharge, revolutionize, amplify,
bolster, catalyze, cultivate, spearhead, underpin, underscore, illuminate,
embark, enhance, showcase, transformative, game-changer, seamless, robust,
cutting-edge, bleeding-edge, groundbreaking, pivotal, crucial, vital, paramount,
indispensable, meticulous, holistic, multifaceted, nuanced, intricate,
comprehensive, invaluable, unparalleled, unprecedented, powerful, profound,
vibrant, boasts, innovative.

**Nouns and imagery:** tapestry, testament, journey, landscape, realm, synergy,
beacon, treasure trove, paradigm shift, key takeaways, valuable insights,
cornerstone, backbone, ecosystem, deep dive.

**Common swaps:** leverage → use · delve into → dig into · utilize → use ·
transformative → the number · seamless → the steps saved · robust → tested ·
elevate → improve · empower → let.

## 8. Business jargon — precision: low alone

navigate (challenges) → handle · unpack → explain · lean into → accept ·
double down → commit · take a step back → reconsider · moving forward → next ·
circle back → revisit · on the same page → agreed · align on → agree ·
socialize → share · bandwidth → time · low-hanging fruit → name them ·
move the needle → name the metric · deep dive → analysis.

## 9. Transition crutches — precision: low alone

`moreover`, `furthermore`, `additionally`, `consequently`, `hence`, `thus`,
`nevertheless`, `nonetheless`, `notably`, `importantly`, `ultimately`,
`overall`, `in many ways`, `when it comes to`, `in terms of`,
`on one hand … on the other hand`, `generally speaking`, `to some extent`,
`needless to say`, `it goes without saying`.

Almost all are deletable. `When it comes to X` and `in terms of X` have a real
fix: make X the subject. "When it comes to safety, the sedan scores well"
becomes "The sedan scores well on safety."

## 10. Hyphenated clichés — precision: low alone

mission-critical, battle-tested, out-of-the-box, enterprise-grade,
best-of-breed, plug-and-play, industry-leading, purpose-built, turn-key,
value-added, first-class, laser-focused, tried-and-true, ready-made,
best-in-class, future-proof, results-driven, customer-centric,
next-generation, end-to-end.

**Do not touch technical compound modifiers**: load-bearing, thin-walled,
strength-to-weight, signal-to-noise, cross-sectional, read-after-write. The test
is whether removing the pair removes information. If it does not, it was slop.

## 11. Filler grammar — precision: low alone

Slop grammar rather than slop vocabulary: verbs turned into noun phrases.

| Padded | Plain |
|---|---|
| will make a decision on | decides |
| conduct an investigation of | investigate |
| provide assistance to | help |
| a large number of | many |
| in close proximity to | near |
| prior to the start of | before |
| during the course of | during |
| on a regular basis | regularly |
| in spite of the fact that | although |
| has the ability to | can |
| in order to | to |
| for all intents and purposes | *delete* |
| the fact of the matter is that | *delete* |
| as many of you already know | *delete* |

## 12. Model dialects — context only

Each model family over-uses its own words. Useful for editing, **useless for
accusation**: a cluster says the prose carries a dialect. It says nothing about
who or what wrote the document.

| Dialect | Favourites |
|---|---|
| Claude-family | genuinely, fascinating, nuanced, refreshingly, quietly powerful, thoughtful |
| GPT-family | game-changer, supercharge, skyrocket, unlock the potential, take X to the next level, dive deeper into |

Single hits mean nothing. Two or more from one column in a short passage is worth
a look.

## 13. Rhythm and cadence — human eye only

No regex catches these. About half the writing tells in the published studies
live here.

- **Uniform sentence rhythm.** Every sentence roughly the same length. Real writing puts a three-word sentence next to a forty-word one.
- **Uniform paragraph length.** Every paragraph one to two sentences of equal weight.
- **Formulaic section shape.** Every section built as claim → three supports → mini-conclusion.
- **Opener repetition.** Every paragraph starting the same way.
- **Polished but empty.** Survives every mechanical check and still tells the reader nothing specific. This is the residue left when hype vocabulary is removed and nothing concrete replaces it.

> Copy that passes every scanner and still says nothing has not been de-slopped.
> It has been sanded.

---

## The removal order

Passes, in this order. Each is faster because the one before it cleared the noise.

1. **Machine artifacts.** Search for `[`, `utm_source`, `cite`, curly quotes. One minute, removes every certain tell.
2. **Templates and phrases.** Delete outright. Do not rewrite.
3. **Structural patterns.** Em dashes, forced triplets, negation frames, closing aphorism.
4. **Word swaps.** Last — they are the smallest part of the problem.
5. **Cut a third.** An AI draft is padded by roughly that much.
6. **Add one specific detail only you could know.** A number, a date, a name. No tool can do this pass, and it is the one that makes the writing yours.

## A warning about automated passes

From [Anbeeld/WRITING.md](https://github.com/Anbeeld/WRITING.md), and worth
repeating on every tool in this list, including mine. A de-slop pass can quietly
distort what you meant:

- certainty changed without evidence (`may` → `will`, `is` → `might be`)
- scope changed (`some` → `most`, `often` → `always`)
- lost negation, conditions, exceptions, or qualifiers
- a sequence converted into a cause
- a reported view converted into your own claim
- dialect, second-language features, or plainness normalized into prestige prose

Check the meaning after any automated pass, including [Slop Score](https://enhancepost.com/slopscore/)
and EnhancePost. A cleaner score that says something you did not mean is a
worse outcome than the slop was.

## Corrections

Every rule here over-fires somewhere. If one hit your writing and was wrong,
[report the false positive](https://github.com/ravsau/awesome-ai-slop-removal/issues/new?template=false-positive.yml).
That is the highest-value contribution to this file, and it is the only way the
precision labels above stay honest.
