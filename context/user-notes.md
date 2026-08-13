# User Notes

Use this file for durable user-provided notes the assistant should remember across sessions.

Good examples:

- product positioning notes
- audience nuances
- brand constraints
- words or claims to avoid
- preferences about tone or content strategy
- important reminders that should not live in the setup checklist

## Rules

- User-owned file: do not overwrite or heavily rewrite it unless the user asks.
- Add short, durable notes rather than long transcripts.
- Prefer bullets grouped by topic.

## Notes

- Add important user guidance here.
- Naming: refer to the product and agent as Sam. 
- Workflow: do not save fact-check or review notes as separate markdown files; incorporate required feedback directly into drafts.
- Draft preference: new articles should read like final publishable pieces for readers, not like SEO process notes or justifications for methodology and exclusions.
- Content strategy: role-based article series mapped to the Candidate/Connector model. Order and audiences:
  1. Candidate guide (current article): "How to Find a Life Partner: A Trust-First Guide for Serious Matrimony" — written for Candidates only.
  2. Parent/family guide (future) — audience: parents and family members helping a son/daughter.
  3. Volunteer matchmaker guide (future) — audience: community members who facilitate introductions.
  4. Local professional matchmaker guide (future) — audience: professional matchmakers.
- Each article in the series targets one audience segment; do not blend audiences in a single piece.
- Writing standard (2026-08-06): every intro needs a hook that gives the reader a reason to keep reading, not just a topic statement.
- Writing standard (2026-08-06): write for a broad, diverse readership — native and non-native English speakers, younger and older readers. Favor plain words, short sentences, and clear structure over anything that assumes fluency or specialist vocabulary.
- Writing standard (2026-08-06): always include a short FAQ section near the end of every article, not just when asked.
- Writing standard (2026-08-06): follow a "less is more" principle — cut anything that doesn't earn its place rather than padding for length.
- Writing standard (2026-08-06): actively check for and remove duplication — the same point should not be made in two different sections.
- File organization (2026-08-07): every post filename gets a zero-padded serial number (SL#) prefix for easy identification/sorting, e.g. `001-how-to-find-a-life-partner-trust-first-guide-2026-08-05.md`. Every language, including the default English one, lives under its own subfolder (`drafts/en/`, `drafts/bn/`, etc.) rather than a flat `drafts/` list, reusing the same SL# and slug across languages. See `docs/article-writing.md` for the full convention and `MEMORY.md` for the SL# registry. Applied to the existing Candidate guide pair on 2026-08-07.
- Writing standard (2026-08-07): avoid the em dash ("—") as a default connector in English drafts. Prefer a comma, a new sentence, a colon, or a semicolon depending on the sentence. A rare em dash for real emphasis is fine; leaning on it throughout a draft is not.
- Writing standard (2026-08-13): the `**Meta Description**` frontmatter field is the app's `excerpt` field, shown in full on the article page (above Key Takeaways), truncated at 200 chars with "…more" on feed cards, and auto-truncated to 155 chars for social/OG previews. Write it as a real hook (~200-250 chars, landing near the 200-char mark at a natural sentence break), not a tight SEO snippet. See `docs/article-writing.md` for the full guidance.
- bn terminology (2026-08-13): use "বিশ্বাস যোগ্য" (not "বিশ্বাসনির্ভর") for "trust-first"/trustworthy framing, including "the person is trustworthy" (e.g. "তিনি বিশ্বাস যোগ্য মানুষ"). Keep "সত্যিকারের" for identity/realness claims (e.g. "a real person stands behind the profile," "real, verifiable people"), those are a different concept and stay as-is.
