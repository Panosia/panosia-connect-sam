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
- File organization (2026-08-07, superseded 2026-08-15): every post filename got a zero-padded serial number (SL#) prefix under a flat `drafts/en/`, `drafts/bn/` split. Replaced by the `posts/<SL#>-<slug>/` page-bundle structure (no date in the name, dates moved to per-language `Draft Date`/`Publish Date` frontmatter; see `docs/article-writing.md` and `MEMORY.md`'s Gaps To Resolve note for the current convention).
- Writing standard (2026-08-07): avoid the em dash ("—") as a default connector in English drafts. Prefer a comma, a new sentence, a colon, or a semicolon depending on the sentence. A rare em dash for real emphasis is fine; leaning on it throughout a draft is not.
- Writing standard (2026-08-13): the `**Meta Description**` frontmatter field is the app's `excerpt` field, shown in full on the article page (above Key Takeaways), truncated at 200 chars with "…more" on feed cards, and auto-truncated to 155 chars for social/OG previews. Write it as a real hook (~200-250 chars, landing near the 200-char mark at a natural sentence break), not a tight SEO snippet. See `docs/article-writing.md` for the full guidance.
- bn terminology (2026-08-13, refined 2026-08-24): use "বিশ্বাস যোগ্য" (not "বিশ্বাসনির্ভর") for "trust-first"/trustworthy framing, including "the person is trustworthy" (e.g. "তিনি বিশ্বাস যোগ্য মানুষ"). Keep "সত্যিকারের" strictly for identity/realness/authenticity claims (e.g. "a real person stands behind the profile," "real, verifiable people," "is this person real?," genuine-vs-scam framing) — those stay as-is. For "genuine/trustworthy relationship" or "who's genuine/reliable" framing (not identity or authenticity), use "নির্ভরযোগ্য" or "বিশ্বাস যোগ্য" instead of "সত্যিকারের", picking whichever reads more naturally in context. Applied across article #1's bn draft on 2026-08-24 (meta description "কে সত্যিকারের" → "কে নির্ভরযোগ্য"; "real relationships" phrasing in 3 places → "নির্ভরযোগ্য সম্পর্ক[ের]").
- Workflow preference (2026-08-14): before writing a full draft, show a paragraph-by-paragraph outline (not just section H2s) for user review and approval first. Wait for sign-off before drafting full prose.
- Article #2 core thesis (2026-08-14, from user): parents have always helped their children marry well through their own informal network, friends, colleague lunch-time conversations, social gatherings, religious gatherings, siblings/cousins' networks, local religious leaders (e.g. an Imam), and local professional matchmakers. Panosia Connect gathers that same trusted network onto one platform (framed like LinkedIn/Facebook did for professional/social networking), so a parent can search within their network, start introductions, and vouch for people they know (and be vouched for in return). Because everyone is part of the same trusted network, a parent who helps their own child ends up able to help others too. This is the central thesis for the parent/family guide; keep the parent as protagonist throughout.
