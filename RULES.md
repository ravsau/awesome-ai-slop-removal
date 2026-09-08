# EnhancePost rule catalog

This file is generated from [`rules.json`](./rules.json) with
`python3 scripts/enhancepost/build_rules.py`. It is a review aid, not an
authorship detector. A finding says that a phrase or formatting pattern is
worth checking. It does not prove who wrote the text.

The catalog was reviewed on **2026-09-07**. General rules cover 12 categories and
the bounded `cover-letter` pilot adds application boilerplate. Formatting
findings include pasted spaces, placeholders, citation tokens, and invisible
characters. They are never treated as proof. Emoji, emoji modifiers, CJK
ideographic spaces, and meaningful multilingual joiners remain intact.

The browser contract is exported by [`rule_engine.js`](./rule_engine.js):

```js
SlopRules.catalog(context = 'general')
SlopRules.findings(text, context = 'general')
SlopRules.applyFinding(text, finding)
```

`findings` returns ordered, non-overlapping spans. `applyFinding` checks that
the span still contains the original text before applying an explicitly safe
replacement. The default is manual review (`replacement: null`,
`allowDelete: false`). The engine makes no score or authorship claim.

## Content artifacts (`artifacts`, formatting)

| ID | Context | Matcher | Review guidance | Replacement |
| --- | --- | --- | --- | --- |
| `general-artifacts-unfilled-placeholder` | `general` | `/\[(?:your name\|insert [a-z ]{2,20}\|company\|date\|todo\|xx\|placeholder\|name\|email\|url\|link)\]/gi` | Formatting or template residue that deserves a manual check; it does not prove who wrote the text. | manual review |
| `general-artifacts-leaked-citation-token` | `general` | `/(?:cite\|video\|image)turn\d+\w*\|oai_citation\|contentReference\|【\d+†[^】]*】/g` | Formatting or template residue that deserves a manual check; it does not prove who wrote the text. | manual review |
| `general-artifacts-chat-tracking-parameter` | `general` | `/https?://[^\s<>"'`()\[\]]+/gi` | This URL action removes only a recognized chat utm_source parameter. It preserves other URL text and does not show who wrote the text. | Remove only recognized chat utm_source parameters; preserve every other query token, encoding, fragment, wrapper, and punctuation. |
| `general-artifacts-invisible-formatting-character` | `general` | `/[\u200B\u200E\u200F\u2060-\u2064\uFEFF\u00AD\u180E\u034F\u061C\u202A-\u202E\u2066-\u2069\u2028\u2029]/g` | Formatting or template residue that deserves a manual check; it does not prove who wrote the text. | manual review |
| `general-artifacts-zero-width-joiner-outside-emoji` | `general` | `/\u200D/g` | Formatting or template residue that deserves a manual check; it does not prove who wrote the text. | manual review |
| `general-artifacts-mixed-script-lookalike-word` | `general` | `/[A-Za-z\u0400-\u04FF\u0370-\u03FF]{2,}/gu` | Formatting or template residue that deserves a manual check; it does not prove who wrote the text. | manual review |

## Pasted typography (`typography`, formatting)

| ID | Context | Matcher | Review guidance | Replacement |
| --- | --- | --- | --- | --- |
| `general-typography-non-standard-space` | `general` | `/[\u00A0\u202F\u2000-\u200A\u205F\u3000]/g` | A pasted-space pattern that can affect search or layout; keep it when the writing system needs it. | manual review |

## Marketing templates (`templates`, style)

| ID | Context | Matcher | Review guidance | Replacement |
| --- | --- | --- | --- | --- |
| `general-templates-unlock-the-full-potential` | `general` | `unlock the full potential` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-navigate-the-complexities` | `general` | `navigate the complexities` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-a-testament-to-the-power-of` | `general` | `a testament to the power of` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-stay-ahead-of-the-curve` | `general` | `stay ahead of the curve` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-turn-challenges-into-opportunities` | `general` | `turn challenges into opportunities` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-working-smarter-not-harder` | `general` | `working smarter, not harder` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-drive-meaningful-impact` | `general` | `drive meaningful impact` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-seamlessly-integrate` | `general` | `seamlessly integrate` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-something-for-everyone` | `general` | `something for everyone` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-more-important-than-ever` | `general` | `more important than ever` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-the-future-is-full-of-possibilities` | `general` | `the future is full of possibilities` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-reimagined` | `general` | `reimagined` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-empowering-teams-to` | `general` | `empowering teams to` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-revolutionizing-the-way` | `general` | `revolutionizing the way` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-unlocks-the-full-potential` | `general` | `unlocks the full potential` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-unlocking-the-full-potential` | `general` | `unlocking the full potential` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-navigating-the-complexities` | `general` | `navigating the complexities` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-navigates-the-complexities` | `general` | `navigates the complexities` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-seamlessly-integrates` | `general` | `seamlessly integrates` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-seamlessly-integrating` | `general` | `seamlessly integrating` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-empowers-teams-to` | `general` | `empowers teams to` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-empower-teams-to` | `general` | `empower teams to` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-revolutionizes-the-way` | `general` | `revolutionizes the way` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-drives-meaningful-impact` | `general` | `drives meaningful impact` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-staying-ahead-of-the-curve` | `general` | `staying ahead of the curve` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |
| `general-templates-turns-challenges-into-opportunities` | `general` | `turns challenges into opportunities` | A reusable promotional frame. Check whether a concrete claim would say more. | manual review |

## Sentence patterns (`sentence`, style)

| ID | Context | Matcher | Review guidance | Replacement |
| --- | --- | --- | --- | --- |
| `general-sentence-weasel-attribution` | `general` | `/\b(?:experts? (?:agree\|say)\|studies show\|research suggests\|scientists believe\|many (?:argue\|believe)\|critics (?:note\|argue)\|observers note\|it is widely (?:regarded\|believed)\|some say)\b/gi` | Phrases such as ‘experts agree’ and ‘studies show’ imply support without naming a source. Cite the source or state the observation without the attribution. | manual review |
| `general-sentence-superficial-ing-tail` | `general` | `/,\s+(?:highlighting\|reflecting\|symbolizing\|emphasizing\|underscoring\|showcasing\|signaling\|demonstrating\|illustrating\|embodying\|reinforcing\|cultivating)\b/gi` | A sentence shape that can weaken a claim when it replaces a source, fact, or clear subject. | manual review |
| `general-sentence-outcome-speculation-tail` | `general` | `/,\s+(?:raising questions about\|sparking debate\|prompting reflection\|with broader implications\|reshaping our understanding\|paving the way for)/gi` | A sentence shape that can weaken a claim when it replaces a source, fact, or clear subject. | manual review |
| `general-sentence-possible-false-range` | `general` | `/\bfrom [a-z]{3,15} to [a-z]{3,15}\b(?![^.]*\b(?:19\|20)\d\d)/gi` | A sentence shape that can weaken a claim when it replaces a source, fact, or clear subject. | manual review |
| `general-sentence-faux-insight-setup` | `general` | `/\bwhat (?:nobody\|no one) tells you\|the part everyone misses\|what most people get wrong\|here\'s what nobody/gi` | A sentence shape that can weaken a claim when it replaces a source, fact, or clear subject. | manual review |
| `general-sentence-question-answer-drama` | `general` | `/\b(?:is it perfect\?\|will it scale\?\|does (?:this\|it) matter\?)\s*(?:no\|yes\|absolutely)\b/gi` | A sentence shape that can weaken a claim when it replaces a source, fact, or clear subject. | manual review |
| `general-sentence-hedge-stacking` | `general` | `/\b(?:may\|might\|could) (?:potentially\|possibly\|perhaps)\b\|\bsomewhat (?:likely\|effective\|similar)\b.*\bin some cases\b/gi` | A sentence shape that can weaken a claim when it replaces a source, fact, or clear subject. | manual review |
| `general-sentence-lazy-extreme` | `general` | `/\b(?:every\|always\|never\|everyone\|nobody\|no one) (?:single )?[a-z]{3,}/gi` | A sentence shape that can weaken a claim when it replaces a source, fact, or clear subject. | manual review |

## Structural patterns (`structural`, style)

| ID | Context | Matcher | Review guidance | Replacement |
| --- | --- | --- | --- | --- |
| `general-structural-em-dash` | `general` | `/(?:\S\s*(?:—\|–\|\s--\s)\s*\S)/g` | A structural habit worth reading aloud. One occurrence can be intentional. | manual review |
| `general-structural-negation-frame` | `general` | `/\b(?:isn\'t\|aren\'t\|doesn\'t\|don\'t\|wasn\'t\|weren\'t\|not)\s+(?:just\|only\|merely\|simply\|about)\s+[^.\n]{2,70}?[,;—–-]\s?(?:it\'s\|it is\|but\|they\'re\|they are\|it\s+[a-z]{2,15}s\b)/gi` | A structural habit worth reading aloud. One occurrence can be intentional. | manual review |
| `general-structural-tailing-negation` | `general` | `/\bno [a-z]{3,12},\s*just [a-z]{3,12}\b/gi` | A structural habit worth reading aloud. One occurrence can be intentional. | manual review |
| `general-structural-rhetorical-question-opener` | `general` | `/\b(?:ever wondered\|have you ever\|what if i told you\|did you know\|ever wonder why)\b/gi` | A structural habit worth reading aloud. One occurrence can be intentional. | manual review |
| `general-structural-summary-recap-ending` | `general` | `/\b(?:in conclusion\|in summary\|to sum up\|to wrap up\|the key takeaway is\|all in all)\b/gi` | A structural habit worth reading aloud. One occurrence can be intentional. | manual review |
| `general-structural-conditional-next-step-menu` | `general` | `/\b(?:if you want,? i can\|let me know if you\'?d like\|i can also help\|if you\'?d like,? i)\b/gi` | A structural habit worth reading aloud. One occurrence can be intentional. | manual review |
| `general-structural-possible-rule-of-three` | `general` | `/\b\w+, \w+,? and \w+\.(?=\s\|$)/g` | A structural habit worth reading aloud. One occurrence can be intentional. | manual review |
| `general-structural-decorative-horizontal-rule` | `general` | `/^\s*(?:---\|\*\*\*\|___)\s*$/gm` | A structural habit worth reading aloud. One occurrence can be intentional. | manual review |
| `general-structural-bold-term-bullet-run` | `general` | `/^\s*[-*]\s+\*\*[^*]{2,40}\*\*\s*:/gm` | A structural habit worth reading aloud. One occurrence can be intentional. | manual review |

## Tell phrases (`phrases`, style)

| ID | Context | Matcher | Review guidance | Replacement |
| --- | --- | --- | --- | --- |
| `general-phrases-thrilled-to-announce` | `general` | `thrilled to announce` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-excited-to-share` | `general` | `excited to share` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-excited-to-announce` | `general` | `excited to announce` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-humbled-and-honored` | `general` | `humbled and honored` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-in-today-s-fast-paced-world` | `general` | `in today's fast-paced world` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-in-today-s-digital-age` | `general` | `in today's digital age` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-in-the-ever-evolving` | `general` | `in the ever-evolving` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-in-a-world-where` | `general` | `in a world where` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-in-an-era-of` | `general` | `in an era of` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-more-than-ever-before` | `general` | `more than ever before` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-let-s-dive-in` | `general` | `let's dive in` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-let-s-delve-into` | `general` | `let's delve into` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-let-s-explore` | `general` | `let's explore` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-picture-this` | `general` | `picture this` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-imagine-a-world-where` | `general` | `imagine a world where` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-the-power-of` | `general` | `the power of` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-it-s-important-to-note` | `general` | `it's important to note` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-it-is-important-to-note` | `general` | `it is important to note` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-it-s-worth-noting` | `general` | `it's worth noting` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-it-bears-mentioning` | `general` | `it bears mentioning` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-one-thing-to-consider` | `general` | `one thing to consider` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-a-key-consideration` | `general` | `a key consideration` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-it-cannot-be-overstated` | `general` | `it cannot be overstated` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-at-the-end-of-the-day` | `general` | `at the end of the day` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-take-it-to-the-next-level` | `general` | `take it to the next level` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-here-s-the-kicker` | `general` | `here's the kicker` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-here-s-the-thing` | `general` | `here's the thing` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-but-here-s-the-thing` | `general` | `but here's the thing` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-make-no-mistake` | `general` | `make no mistake` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-let-s-be-honest` | `general` | `let's be honest` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-the-truth-is` | `general` | `the truth is` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-in-reality` | `general` | `in reality` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-at-its-core` | `general` | `at its core` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-fundamentally-speaking` | `general` | `fundamentally speaking` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-the-real-question-is` | `general` | `the real question is` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-the-heart-of-the-matter` | `general` | `the heart of the matter` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-let-that-sink-in` | `general` | `let that sink in` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-read-that-again` | `general` | `read that again` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-this-comprehensive-guide` | `general` | `this comprehensive guide` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-everything-you-need-to-know` | `general` | `everything you need to know` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-whether-you-re-a-beginner` | `general` | `whether you're a beginner` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-the-future-is-bright` | `general` | `the future is bright` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-let-s-build-it-together` | `general` | `let's build it together` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-feel-free-to-reach-out` | `general` | `feel free to reach out` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-hope-this-helps` | `general` | `hope this helps` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-great-question` | `general` | `great question` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-as-an-ai-language-model` | `general` | `as an ai language model` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `general-phrases-as-of-my-last-knowledge-update` | `general` | `as of my last knowledge update` | A stock phrase that may be unnecessary in edited prose. Keep it when it carries your meaning. | manual review |
| `cover-letter-i-am-writing-to-apply-for-the-position-of` | `cover-letter` | `I am writing to apply for the position of` | Start with the role or the specific reason you want this job. This is a bounded cover-letter review, not a prohibition. | manual review |
| `cover-letter-i-believe-i-am-the-perfect-candidate` | `cover-letter` | `I believe I am the perfect candidate` | Name the first problem you would fix or build. This is a bounded cover-letter review, not a prohibition. | manual review |
| `cover-letter-motivated-organized-results-driven-professional` | `cover-letter` | `motivated, organized, results-driven professional` | Give one result with a number. This is a bounded cover-letter review, not a prohibition. | manual review |
| `cover-letter-hard-working-team-player` | `cover-letter` | `hard-working team player` | Name the team and what shipped. This is a bounded cover-letter review, not a prohibition. | manual review |
| `cover-letter-highly-motivated-and-detail-oriented` | `cover-letter` | `highly motivated and detail-oriented` | Tell the story of one thing you caught. This is a bounded cover-letter review, not a prohibition. | manual review |
| `cover-letter-passionate-about-industry` | `cover-letter` | `passionate about [industry]` | Point to a project you did without being asked. This is a bounded cover-letter review, not a prohibition. | manual review |
| `cover-letter-i-am-thrilled-to-apply` | `cover-letter` | `I am thrilled to apply` | State the real reason you want this job. This is a bounded cover-letter review, not a prohibition. | manual review |
| `cover-letter-your-esteemed-organization` | `cover-letter` | `your esteemed organization` | Name the company. This is a bounded cover-letter review, not a prohibition. | manual review |
| `cover-letter-proven-track-record-of-success` | `cover-letter` | `proven track record of success` | State one metric. This is a bounded cover-letter review, not a prohibition. | manual review |
| `cover-letter-cross-functional-collaboration` | `cover-letter` | `cross-functional collaboration` | Name the teams and what happened between them. This is a bounded cover-letter review, not a prohibition. | manual review |
| `cover-letter-leveraged-agile-methodologies` | `cover-letter` | `leveraged agile methodologies` | Name the actual process and what it changed. This is a bounded cover-letter review, not a prohibition. | manual review |
| `cover-letter-synergy-between-stakeholders` | `cover-letter` | `synergy between stakeholders` | Name the people and the decision they reached. This is a bounded cover-letter review, not a prohibition. | manual review |
| `cover-letter-please-do-not-hesitate-to-contact-me` | `cover-letter` | `please do not hesitate to contact me` | Use a direct close if you need one. This is a bounded cover-letter review, not a prohibition. | manual review |
| `cover-letter-i-look-forward-to-hearing-from-you` | `cover-letter` | `I look forward to hearing from you` | Cut it or name a real follow-up date. This is a bounded cover-letter review, not a prohibition. | manual review |

## Brochure register (`brochure`, style)

| ID | Context | Matcher | Review guidance | Replacement |
| --- | --- | --- | --- | --- |
| `general-brochure-nestled` | `general` | `nestled` | Praise without a stated observation. Replace it only when you can name the evidence. | manual review |
| `general-brochure-in-the-heart-of` | `general` | `in the heart of` | Praise without a stated observation. Replace it only when you can name the evidence. | manual review |
| `general-brochure-picturesque` | `general` | `picturesque` | Praise without a stated observation. Replace it only when you can name the evidence. | manual review |
| `general-brochure-charming` | `general` | `charming` | Praise without a stated observation. Replace it only when you can name the evidence. | manual review |
| `general-brochure-idyllic` | `general` | `idyllic` | Praise without a stated observation. Replace it only when you can name the evidence. | manual review |
| `general-brochure-quaint` | `general` | `quaint` | Praise without a stated observation. Replace it only when you can name the evidence. | manual review |
| `general-brochure-breathtaking` | `general` | `breathtaking` | Praise without a stated observation. Replace it only when you can name the evidence. | manual review |
| `general-brochure-must-visit` | `general` | `must-visit` | Praise without a stated observation. Replace it only when you can name the evidence. | manual review |
| `general-brochure-renowned` | `general` | `renowned` | Praise without a stated observation. Replace it only when you can name the evidence. | manual review |
| `general-brochure-acclaimed` | `general` | `acclaimed` | Praise without a stated observation. Replace it only when you can name the evidence. | manual review |
| `general-brochure-world-class` | `general` | `world-class` | Praise without a stated observation. Replace it only when you can name the evidence. | manual review |
| `general-brochure-best-in-class` | `general` | `best-in-class` | Praise without a stated observation. Replace it only when you can name the evidence. | manual review |
| `general-brochure-top-tier` | `general` | `top-tier` | Praise without a stated observation. Replace it only when you can name the evidence. | manual review |
| `general-brochure-premier` | `general` | `premier` | Praise without a stated observation. Replace it only when you can name the evidence. | manual review |
| `general-brochure-industry-leading` | `general` | `industry-leading` | Praise without a stated observation. Replace it only when you can name the evidence. | manual review |
| `general-brochure-state-of-the-art` | `general` | `state-of-the-art` | Praise without a stated observation. Replace it only when you can name the evidence. | manual review |
| `general-brochure-simple-yet` | `general` | `simple yet` | Praise without a stated observation. Replace it only when you can name the evidence. | manual review |

## Tell words (`words`, style)

| ID | Context | Matcher | Review guidance | Replacement |
| --- | --- | --- | --- | --- |
| `general-words-delve` | `general` | `delve` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-leverage` | `general` | `leverage` | This business verb can hide the tool or action. Use it only when it names what was applied; plain ‘use’ is often clearer. | use |
| `general-words-unlock` | `general` | `unlock` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-unleash` | `general` | `unleash` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-unveil` | `general` | `unveil` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-elevate` | `general` | `elevate` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-empower` | `general` | `empower` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-foster` | `general` | `foster` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-harness` | `general` | `harness` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-streamline` | `general` | `streamline` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-supercharge` | `general` | `supercharge` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-revolutionize` | `general` | `revolutionize` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-amplify` | `general` | `amplify` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-bolster` | `general` | `bolster` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-catalyze` | `general` | `catalyze` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-cultivate` | `general` | `cultivate` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-spearhead` | `general` | `spearhead` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-underpin` | `general` | `underpin` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-underscore` | `general` | `underscore` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-illuminate` | `general` | `illuminate` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-embark` | `general` | `embark` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-enhance` | `general` | `enhance` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-showcase` | `general` | `showcase` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-transformative` | `general` | `transformative` | This adjective claims large change without showing the before and after. State the result, or keep it when evidence supports it. | manual review |
| `general-words-game-changer` | `general` | `game-changer` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-game-changer-2` | `general` | `game changer` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-seamless` | `general` | `seamless` | This adjective hides integration steps or failure modes. Name what connected and what users experienced. | manual review |
| `general-words-robust` | `general` | `robust` | This adjective claims reliability without the test or condition. Name the failure it prevents, or keep it when you can support it. | manual review |
| `general-words-cutting-edge` | `general` | `cutting-edge` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-bleeding-edge` | `general` | `bleeding-edge` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-groundbreaking` | `general` | `groundbreaking` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-pivotal` | `general` | `pivotal` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-crucial` | `general` | `crucial` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-paramount` | `general` | `paramount` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-indispensable` | `general` | `indispensable` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-meticulous` | `general` | `meticulous` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-meticulously` | `general` | `meticulously` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-holistic` | `general` | `holistic` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-multifaceted` | `general` | `multifaceted` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-nuanced` | `general` | `nuanced` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-intricate` | `general` | `intricate` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-comprehensive` | `general` | `comprehensive` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-invaluable` | `general` | `invaluable` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-unparalleled` | `general` | `unparalleled` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-unprecedented` | `general` | `unprecedented` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-profound` | `general` | `profound` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-vibrant` | `general` | `vibrant` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-boasts` | `general` | `boasts` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-innovative` | `general` | `innovative` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-tapestry` | `general` | `tapestry` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-testament` | `general` | `testament` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-landscape` | `general` | `landscape` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-realm` | `general` | `realm` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-synergy` | `general` | `synergy` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-beacon` | `general` | `beacon` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-treasure-trove` | `general` | `treasure trove` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-paradigm-shift` | `general` | `paradigm shift` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-key-takeaways` | `general` | `key takeaways` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-valuable-insights` | `general` | `valuable insights` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-cornerstone` | `general` | `cornerstone` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-backbone` | `general` | `backbone` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-ecosystem` | `general` | `ecosystem` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |
| `general-words-deep-dive` | `general` | `deep dive` | A real word that can become vague or inflated in dense clusters. Review the surrounding claim. | manual review |

## Business jargon (`jargon`, style)

| ID | Context | Matcher | Review guidance | Replacement |
| --- | --- | --- | --- | --- |
| `general-jargon-unpack` | `general` | `unpack` | Workplace shorthand. Keep it when the audience uses it and it names a precise action. | manual review |
| `general-jargon-lean-into` | `general` | `lean into` | Workplace shorthand. Keep it when the audience uses it and it names a precise action. | manual review |
| `general-jargon-double-down` | `general` | `double down` | Workplace shorthand. Keep it when the audience uses it and it names a precise action. | manual review |
| `general-jargon-take-a-step-back` | `general` | `take a step back` | Workplace shorthand. Keep it when the audience uses it and it names a precise action. | manual review |
| `general-jargon-moving-forward` | `general` | `moving forward` | Workplace shorthand. Keep it when the audience uses it and it names a precise action. | manual review |
| `general-jargon-circle-back` | `general` | `circle back` | Workplace shorthand. Keep it when the audience uses it and it names a precise action. | manual review |
| `general-jargon-on-the-same-page` | `general` | `on the same page` | Workplace shorthand. Keep it when the audience uses it and it names a precise action. | manual review |
| `general-jargon-socialize` | `general` | `socialize` | Workplace shorthand. Keep it when the audience uses it and it names a precise action. | manual review |
| `general-jargon-bandwidth` | `general` | `bandwidth` | Workplace shorthand. Keep it when the audience uses it and it names a precise action. | manual review |
| `general-jargon-low-hanging-fruit` | `general` | `low-hanging fruit` | Workplace shorthand. Keep it when the audience uses it and it names a precise action. | manual review |
| `general-jargon-move-the-needle` | `general` | `move the needle` | Workplace shorthand. Keep it when the audience uses it and it names a precise action. | manual review |

## Transition crutches (`crutches`, style)

| ID | Context | Matcher | Review guidance | Replacement |
| --- | --- | --- | --- | --- |
| `general-crutches-moreover` | `general` | `moreover` | A transition that may add little. Remove it only if the sentence still links clearly. | manual review |
| `general-crutches-furthermore` | `general` | `furthermore` | A transition that may add little. Remove it only if the sentence still links clearly. | manual review |
| `general-crutches-additionally` | `general` | `additionally` | A transition that may add little. Remove it only if the sentence still links clearly. | manual review |
| `general-crutches-consequently` | `general` | `consequently` | A transition that may add little. Remove it only if the sentence still links clearly. | manual review |
| `general-crutches-hence` | `general` | `hence` | A transition that may add little. Remove it only if the sentence still links clearly. | manual review |
| `general-crutches-nevertheless` | `general` | `nevertheless` | A transition that may add little. Remove it only if the sentence still links clearly. | manual review |
| `general-crutches-nonetheless` | `general` | `nonetheless` | A transition that may add little. Remove it only if the sentence still links clearly. | manual review |
| `general-crutches-notably` | `general` | `notably` | A transition that may add little. Remove it only if the sentence still links clearly. | manual review |
| `general-crutches-ultimately` | `general` | `ultimately` | A transition that may add little. Remove it only if the sentence still links clearly. | manual review |
| `general-crutches-overall` | `general` | `overall` | A transition that may add little. Remove it only if the sentence still links clearly. | manual review |
| `general-crutches-in-many-ways` | `general` | `in many ways` | A transition that may add little. Remove it only if the sentence still links clearly. | manual review |
| `general-crutches-when-it-comes-to` | `general` | `when it comes to` | A transition that may add little. Remove it only if the sentence still links clearly. | manual review |
| `general-crutches-in-terms-of` | `general` | `in terms of` | A transition that may add little. Remove it only if the sentence still links clearly. | manual review |
| `general-crutches-on-the-other-hand` | `general` | `on the other hand` | A transition that may add little. Remove it only if the sentence still links clearly. | manual review |
| `general-crutches-generally-speaking` | `general` | `generally speaking` | A transition that may add little. Remove it only if the sentence still links clearly. | manual review |
| `general-crutches-to-some-extent` | `general` | `to some extent` | A transition that may add little. Remove it only if the sentence still links clearly. | manual review |
| `general-crutches-needless-to-say` | `general` | `needless to say` | A transition that may add little. Remove it only if the sentence still links clearly. | manual review |
| `general-crutches-it-goes-without-saying` | `general` | `it goes without saying` | A transition that may add little. Remove it only if the sentence still links clearly. | manual review |

## Hyphenated cliches (`hyphen`, style)

| ID | Context | Matcher | Review guidance | Replacement |
| --- | --- | --- | --- | --- |
| `general-hyphen-mission-critical` | `general` | `mission-critical` | A familiar compound adjective. Check whether the noun or result is more precise. | manual review |
| `general-hyphen-battle-tested` | `general` | `battle-tested` | A familiar compound adjective. Check whether the noun or result is more precise. | manual review |
| `general-hyphen-out-of-the-box` | `general` | `out-of-the-box` | A familiar compound adjective. Check whether the noun or result is more precise. | manual review |
| `general-hyphen-enterprise-grade` | `general` | `enterprise-grade` | A familiar compound adjective. Check whether the noun or result is more precise. | manual review |
| `general-hyphen-best-of-breed` | `general` | `best-of-breed` | A familiar compound adjective. Check whether the noun or result is more precise. | manual review |
| `general-hyphen-plug-and-play` | `general` | `plug-and-play` | A familiar compound adjective. Check whether the noun or result is more precise. | manual review |
| `general-hyphen-purpose-built` | `general` | `purpose-built` | A familiar compound adjective. Check whether the noun or result is more precise. | manual review |
| `general-hyphen-turn-key` | `general` | `turn-key` | A familiar compound adjective. Check whether the noun or result is more precise. | manual review |
| `general-hyphen-value-added` | `general` | `value-added` | A familiar compound adjective. Check whether the noun or result is more precise. | manual review |
| `general-hyphen-laser-focused` | `general` | `laser-focused` | A familiar compound adjective. Check whether the noun or result is more precise. | manual review |
| `general-hyphen-tried-and-true` | `general` | `tried-and-true` | A familiar compound adjective. Check whether the noun or result is more precise. | manual review |
| `general-hyphen-ready-made` | `general` | `ready-made` | A familiar compound adjective. Check whether the noun or result is more precise. | manual review |
| `general-hyphen-future-proof` | `general` | `future-proof` | A familiar compound adjective. Check whether the noun or result is more precise. | manual review |
| `general-hyphen-results-driven` | `general` | `results-driven` | This adjective claims a focus on results without naming one. State the result and metric when you have them. | manual review |
| `general-hyphen-customer-centric` | `general` | `customer-centric` | A familiar compound adjective. Check whether the noun or result is more precise. | manual review |
| `general-hyphen-next-generation` | `general` | `next-generation` | A familiar compound adjective. Check whether the noun or result is more precise. | manual review |
| `general-hyphen-end-to-end` | `general` | `end-to-end` | A familiar compound adjective. Check whether the noun or result is more precise. | manual review |

## Filler grammar (`filler`, style)

| ID | Context | Matcher | Review guidance | Replacement |
| --- | --- | --- | --- | --- |
| `general-filler-make-a-decision-on` | `general` | `make a decision on` | The noun ‘decision’ repeats the action in ‘make’. ‘Decide on’ keeps the same object and meaning in a complete sentence. | decide on |
| `general-filler-conduct-an-investigation` | `general` | `conduct an investigation` | A longer phrase that may hide a shorter verb. Preserve the meaning when editing. | manual review |
| `general-filler-provide-assistance-to` | `general` | `provide assistance to` | The noun ‘assistance’ can become the direct verb ‘help’. Check that the following person or team is the same object. | help |
| `general-filler-a-large-number-of` | `general` | `a large number of` | A longer phrase that may hide a shorter verb. Preserve the meaning when editing. | manual review |
| `general-filler-in-close-proximity-to` | `general` | `in close proximity to` | This phrase adds ‘close’ and ‘proximity’ around the same location. ‘Near’ preserves the relationship without changing the place. | near |
| `general-filler-prior-to-the-start-of` | `general` | `prior to the start of` | This phrase repeats the idea of an earlier start. ‘Before’ preserves the time relationship when followed by the same event. | before |
| `general-filler-during-the-course-of` | `general` | `during the course of` | ‘During’ already expresses the time span. Keep the same noun or event after the shorter preposition. | during |
| `general-filler-on-a-regular-basis` | `general` | `on a regular basis` | This phrase can become the adverb ‘regularly’. Check that the sentence still describes repeated action, not a fixed schedule. | regularly |
| `general-filler-in-spite-of-the-fact-that` | `general` | `in spite of the fact that` | This phrase introduces a contrast with extra nouns. ‘Although’ preserves that contrast when the following clause stays intact. | although |
| `general-filler-for-all-intents-and-purposes` | `general` | `for all intents and purposes` | A longer phrase that may hide a shorter verb. Preserve the meaning when editing. | manual review |
| `general-filler-the-fact-of-the-matter-is` | `general` | `the fact of the matter is` | A longer phrase that may hide a shorter verb. Preserve the meaning when editing. | manual review |
| `general-filler-in-a-manner-of-speaking` | `general` | `in a manner of speaking` | A longer phrase that may hide a shorter verb. Preserve the meaning when editing. | manual review |
| `general-filler-as-many-of-you-already-know` | `general` | `as many of you already know` | A longer phrase that may hide a shorter verb. Preserve the meaning when editing. | manual review |
| `general-filler-with-regard-to` | `general` | `with regard to` | A longer phrase that may hide a shorter verb. Preserve the meaning when editing. | manual review |
| `general-filler-has-the-ability-to` | `general` | `has the ability to` | This phrase can state a capability with the modal verb ‘can’. Keep it when the sentence needs a different emphasis or tense. | can |
| `general-filler-in-order-to` | `general` | `in order to` | ‘To’ already introduces the purpose clause. Keep the same subject and verb after the shorter form. | to |


## Worked review

Hypothetical example (the facts are supplied in the draft):

> We are thrilled to announce a transformative update that unlocks the full
> potential of our platform. The weekly report takes 40 minutes and the update
> cuts it to 6.

After:

> The update adds bulk export. It cuts the weekly report from 40 minutes to 6.

The replacement adds observed detail. The rule engine can identify the phrases,
but it must not invent the number, feature, or outcome.

## Legitimate-use example

> The team leveraged the existing API to migrate 18,000 records.

The word may be acceptable when the surrounding sentence gives precise facts.
Review the whole sentence before changing it.

## Source notes

The catalog preserves the existing search title and public reference links.
The rule vocabulary is a deterministic editorial list, informed by public
anti-slop projects including [humanizer](https://github.com/blader/humanizer),
[stop-slop](https://github.com/hardikpandya/stop-slop),
[no-ai-slop](https://github.com/petergyang/no-ai-slop),
[sloptrim](https://github.com/seyedehsanhadi/sloptrim),
[slopless](https://github.com/berelevant-ai/slopless), and
[slop-guard](https://github.com/eric-tramel/slop-guard). These links are
background sources, not evidence that a matched phrase has one cause.
