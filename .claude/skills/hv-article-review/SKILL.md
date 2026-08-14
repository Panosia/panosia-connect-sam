---
name: hv-article-review
description: Multi-persona readability and publish-readiness review of a draft article — reads the same draft through six-plus distinct reader lenses (native English reader, diaspora/immigrant English reader, young reader, divorced mid-age reader, someone unfamiliar with Panosia Connect, and an industry-leading editor) plus supporting structural checks, then applies editorial judgment and returns one consolidated, actionable review. Use when the user invokes /hv-article-review or asks for a persona-based or multi-reader review of a draft.
---

You are running a multi-persona article review, then acting as the piece's editor to decide what actually belongs in it. The personas are a way of gathering findings, not a report format. The goal is one consolidated, actionable review, not six separate reviews, not a raw findings dump, and not a saved audit file. Light polish is secondary; a publish-ready draft is the goal.

## Usage

`/hv-article-review <path-to-draft> [--keyword "primary keyword"]`

If no path is given, ask which draft to review, or use the most recently drafted/edited file in `drafts/` if the conversation makes that obvious. If no keyword is given, pull `Primary Keyword` from the draft's frontmatter.

## Setup

Read before reviewing:

- The target draft in full.
- `context/brand-voice.md`, `context/user-notes.md`, `context/seo-guidelines.md`
- `context/site-profile.md` (needed to judge the "unfamiliar with Panosia Connect" persona accurately, and to fact-check any product claims that slip in)
- `docs/article-writing.md` and `docs/article-review.md` (house writing and review rules)
- `context/target-keywords.md` and `context/internal-links.md` only if they materially affect the review

Run `node ./scripts/analyze-draft.mjs <path> --keyword "..."` if a keyword is available, and use it as deterministic support, not the only source of truth.

Assume deep fact-checking has already run separately (per the standard `article-writer` → `fact-checker` → `seo-reviewer` workflow) unless told otherwise. Still flag anything that looks unsupported, invented, or risky.

## The Six Required Personas

Read the draft once fully, then re-read it through each lens below. For each persona, capture only what's distinctive to that lens — friction points, confusion, drop-off risk, trust reaction, or a place they'd stop reading. Don't repeat the same observation under multiple personas; note it once, under whichever persona it hits hardest.

1. **Native English reader.** Judge voice, rhythm, and whether anything reads as stiff, over-explained, or translated-sounding. This reader has the highest bar for prose quality and will notice filler, throat-clearing, or awkward phrasing first.
2. **Diaspora / immigrant English reader.** Judge plain language, idioms, sentence length, and cultural assumptions (foods, holidays, wedding customs, family structures) that might not land the same way across regions or generations. This is the project's actual core audience — weight this persona's findings heavily.
3. **Young reader.** Judge whether the piece feels relevant and current to someone earlier in life or newer to the topic (e.g. a younger Candidate, or a young adult reading on behalf of a parent). Flag anything that reads as written only for an older audience, or that assumes lived experience the reader may not have yet.
4. **Divorced, mid-age reader.** Judge whether the piece unintentionally excludes or mishandles someone who isn't a first-time, young, never-married searcher. Flag first-marriage-only assumptions, tone that could feel judgmental or naive to someone with more life experience, and any place the piece would benefit from (without forcing) language that doesn't assume this is the reader's first search for a partner.
5. **Reader unfamiliar with Panosia Connect.** Judge whether the piece is self-contained: does it explain Candidate, Connector, verification, and any other product term in plain language on first use, or does it assume prior familiarity? Flag any sentence that only makes sense to someone who already knows the platform.
6. **Industry-leading editor (Forbes / New York Times caliber).** Judge structure, headline and subhead quality, opening strength, sentence-level craft, cliché density, and whether claims are earned or asserted. This is the harshest craft lens: flag throat-clearing intros, weak verbs, generic advice-listicle phrasing, and anywhere the piece would get cut for not saying enough with its words.

## Additional Lenses (recommended, not user-mandated — apply when relevant)

These extend the persona set. Include them when the draft's topic makes them relevant; skip silently rather than forcing a finding where none exists.

- **Scam-wary / previously burned reader.** Someone who has personally encountered or knows someone who encountered a matrimony scam. Judge whether trust and safety claims feel earned and specific rather than reassuring-sounding filler, and whether the piece could read as naive to this reader.
- **Interfaith / cross-cultural reader.** Judge whether religious and cultural references (e.g. an Imam, specific gathering types, specific customs) read as illustrative examples rather than the only valid path, so readers from other faiths or traditions don't feel unaddressed.
- **Low-tech-literacy / mobile skimmer.** Judge scannability on a small screen: paragraph length, whether the first screen's worth of content orients the reader, and whether headings alone tell a coherent story if that's all someone reads.
- **Legal/compliance-conscious reader.** Cross-check against `context/brand-voice.md`'s claims-to-avoid list (success rates, "safest" absolutes, guarantees). This lens exists to catch overclaiming the fact-checker pass might not flag as factually wrong but that's still risky to publish.
- **Competitor / industry insider.** Someone who works at another matchmaking or dating platform. Judge whether differentiation claims are fair, specific, and non-defensive rather than vague positioning.

Feel free to note if you think another lens materially matters for this specific draft (e.g. a bn-translation-readiness lens for pieces likely to be translated soon) and say why, but don't pad the review with lenses that produce nothing.

## Structural Checks (apply regardless of persona)

- Opening strength: does it orient the reader (audience, problem, promise) within roughly the first 120-150 words, per `docs/article-review.md`?
- Heading hierarchy and scannability.
- Keyword placement without stuffing; title/meta quality.
- Duplication within the piece and against other drafts in the same series (check `drafts/en/` for overlapping ground already covered).
- Em dash overuse as a default connector (project style avoids leaning on it).
- Brand voice and vocabulary alignment (`context/brand-voice.md`'s preferred/avoided terms).
- Research-note leakage: methodology, inclusion criteria, or exclusion lists that don't earn their place for the reader.
- FAQ presence and quality (required per house style).
- Internal links: relevance and whether slugs need live-sitemap verification before publish (flag if unverified).

## Triage Before You Present Anything

Gather all persona and structural findings first, but treat that raw list as working notes, not the deliverable. Before writing anything for the user, go through it yourself and sort each finding into one of three buckets:

1. **Real fixes.** Anything a reader would actually trip on, or anything required by house rules (`brand-voice.md`, `article-writing.md`, factual/claims risk). This includes findings that started out as "optional polish" but are cheap, clearly correct, and improve the piece, fold those in as fixes rather than presenting them as a separate lesser tier.
2. **Deliberately skipped.** Suggestions that are technically valid but would hurt the piece more than help it, duplicate ground another article already owns, trade a concrete detail for a box-checking gesture, or add scope the article doesn't need. Keep these, but only to explain briefly why they're being passed on, not as an open menu of things the user has to individually approve or reject.
3. **Not worth mentioning.** Nitpicks, restatements, or minor stylistic disagreements with no real reader cost either way. Drop these entirely. A consolidated review that lists ten harmless non-issues is worse than one that lists three real ones.

Use your judgment the way an author reviewing their own edited draft would: accommodate what genuinely improves the piece, and drop or override suggestions that don't serve the reader, even if a persona lens raised them. When two personas conflict (e.g. the editor lens wants tighter prose, the diaspora lens wants more plain-language scaffolding), resolve it yourself and say which way you went and why, rather than presenting the conflict unresolved.

## How to Present Findings

Present one consolidated, actionable list, not a per-persona report.

- Lead with the verdict and a one-line summary of what the draft needs.
- List the real fixes (bucket 1) as a short, prioritized checklist. Attribute a fix to the persona/lens that surfaced it only when that context helps the fix make sense, not as a running label on every line.
- Note convergent findings (3+ lenses landing on the same issue) as the highest priority within that list, not as a separate section.
- Give deliberately-skipped items (bucket 2) one line each: what was raised, why it's being passed on. Keep this short. It exists so the user can override a judgment call, not so every persona gets a turn.
- Leave bucket 3 out entirely. Don't summarize what you decided not to mention.
- Describe the underlying reader problem rather than reviewer-facing phrasing that could be copy-pasted straight into the draft.
- Return findings in-session. Do not save a separate review markdown file.
- End with one short verdict label: `publish-ready`, `publish after required fixes`, or `needs substantial revision`.

## Applying Fixes

- Default to a light, surgical pass unless the user clearly wants a deeper rewrite.
- Route the consolidated fix list back into the draft directly (via `article-writer` for substantive prose changes, or a direct edit for small, mechanical fixes) rather than parking them in a separate review artifact.
- Save durable feedback about tone, persona blind spots, or recurring issues to `context/user-notes.md` so future drafts start ahead of them.
