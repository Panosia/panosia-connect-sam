---
name: sam-article-review
description: Independent, multi-persona publish-readiness review of a draft article — reader lenses (native English, ESL/diaspora, young, older/life-experienced, unfamiliar-with-the-product, industry editor) plus SEO/structure checks (intent, headings, metadata, linking, duplication). Produces one consolidated, actionable review with a verdict. Use for a final review pass on a draft, before publishing.
---

Gather findings through personas and SEO/structure checks; report as one editor, not a panel. Output is one consolidated, actionable review, never a raw findings dump per lens.

**Getting the draft and context**: if Notion MCP tools are available, query the "Blog Posts" database for the named post (SL# or title) and fetch its draft content directly, and pull "🎤 Brand Voice" and "🔍 SEO Guidelines & Keywords" from the "🧭 Sam Workspace Memory" hub for house rules and primary keyword instead of asking. Otherwise, ask the user to paste the draft in full, plus (if they have it) their brand voice notes and primary keyword.

Assume deep fact-checking already happened upstream (see the companion `sam-fact-checker` skill) unless told otherwise — still flag anything unsupported, invented, or risky that you spot.

## Personas

Read the draft once fully, then once per lens below. Per persona, note only what's distinctive to that lens; never log the same observation under two personas, it belongs to whichever lens hits it hardest.

**Required (all six, every run):**

| Persona | Judges |
|---|---|
| Native English reader | Voice, rhythm, filler, stiff or translated-sounding phrasing. Highest bar for prose quality. |
| ESL / diaspora reader | Plain language, idioms, phrasal verbs, clause-stacked sentences, passive voice, cultural assumptions. Treat as the default reader, not an edge case — weight heavily. |
| Young / newer-to-topic reader | Relevance to someone earlier in life or newer to the topic; flags content written only for an older/expert audience. |
| Reader with more life experience than the article assumes | First-time-only or textbook assumptions; tone that reads as judgmental or naive to someone who's been through more. |
| Unfamiliar with the product/brand | Self-containment — every product term defined in plain language on first use. |
| Industry-leading editor (Forbes/NYT caliber) | Structure, headline/subhead craft, opening strength, cliché density, earned vs. asserted claims. The harshest lens. |

**Supporting (apply only when the draft's topic makes them relevant; skip silently otherwise):** scam-wary reader (trust/safety claims earned and specific, not reassuring filler); interfaith/cross-cultural reader (religious/cultural references read as illustrative, not the only valid path); low-tech-literacy/mobile skimmer (scannability, headings alone tell a coherent story); legal/compliance-conscious reader (claims-to-avoid list: success rates, "safest" absolutes, guarantees); competitor/industry insider (differentiation claims fair, specific, non-defensive).

Add another lens only if it would surface something none of the above catches, and say why. Don't pad the review with lenses that produce nothing.

## SEO / Structural Checks

- Opening strength: does it reach the reader/problem/promise within ~120-150 words, or does it explain the article/justify the writing approach first?
- Search intent alignment and reader usefulness.
- Title and meta description quality (concrete benefit, not repeating the title word-for-word).
- Heading hierarchy: one clear H1 sense, H2s for major sections, H3s only when they add clarity.
- Keyword placement without stuffing.
- Citation quality and link relevance; internal links only if genuinely relevant (never invent a URL — flag "needs a real link" instead of inventing one).
- Duplication: a point, example, or mechanic restated across sections without doing new work.
- Em dash overuse as a default connector, instead of a comma, period, colon, or semicolon.
- Research-note or methodology leakage (inclusion criteria, exclusion notes, "how we picked this list") that doesn't help the reader decide.
- FAQ presence.
- Brand voice/vocabulary alignment, if the user supplied brand notes.

## Triage

Before writing anything for the user, sort every finding into exactly one bucket:

1. **Fix.** Anything a reader would actually trip on, or required by house rules or claims risk. Fold in cheap, clearly-correct "optional polish" as a fix rather than a lesser tier.
2. **Deliberately skipped.** Valid but not worth taking (duplicates ground another piece owns, trades a concrete detail for a box-checking gesture, adds unneeded scope). One line explaining why, so the user can overrule it.
3. **Drop.** Nitpicks and stylistic disagreements with no real reader cost — don't mention these at all.

Resolve persona conflicts yourself (e.g. editor lens wants tighter prose, ESL lens wants more scaffolding) and state which way you went and why. Convergent findings (3+ lenses, same issue) are the top-priority fixes.

## Output

1. Verdict + one-line summary of what the draft needs, first.
2. Fixes as a short prioritized checklist, phrased as the reader problem, not copy-pasteable reviewer wording. Cite the persona only when it helps a fix make sense.
3. Skipped items, one line each.
4. Nothing else — no separate saved review file, this is an in-reply review.

Verdict labels:

- `publish-ready` — no fixes.
- `publish after required fixes` — fixes exist but are light/mechanical (wording, metadata, a defined term, a trimmed redundancy).
- `needs substantial revision` — fixes require structural change, a thesis gap, or unresolved factual/claims risk.
