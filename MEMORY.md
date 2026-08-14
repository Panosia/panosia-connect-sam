# Sam Memory

This file tracks setup state and working assumptions so new sessions can orient quickly.
Update it whenever setup progress or core strategy assumptions change.

## Onboarding Status

- Overall status: Good enough
- Last updated: 2026-08-05

### Required Setup Checklist

- [x] Company basics and offer
- [x] Audience and content goals
- [x] Brand voice and messaging rules
- [x] Optional research data integration decision (skipped for now)
- [x] Starter target keywords

### Optional Advanced Setup

- [ ] Internal links

## Current Known Context

- Company: Panosia Connect (Panosia LLC)
- Website: https://connect.panosia.com
- Product or service: Trust-based marriage/matchmaking platform with Candidate and Connector roles
- Main offer: Free-to-join platform (no subscriptions); optional one-time verification services are the only paid products
- Primary audience: Adults seeking a life partner (Candidates) plus family/community introducers (Connectors); English + Bengali markets
- Main content goal: Organic acquisition for matrimony/trust queries; convert to signup, network building, and optional verification
- External research data preference: Skip for now (user decision, 2026-08-05)
- External research data status: Declined for now; can revisit later
- DataForSEO setup timing: Not needed for now

## Gaps To Resolve

- Internal links map is optional and can be deferred.
- Keyword map is a first pass; refine with real search data later if desired (DataForSEO can be revisited).
- New file-naming convention (2026-08-07): every post gets an SL# prefix, and every language (including English) lives under its own subfolder (`drafts/en/`, `drafts/bn/`, etc.) instead of a flat `drafts/` list. Applied to the existing pair on 2026-08-07 (see Content Index).

## Content Index (SL#)

Tracks the next available serial number and the SL# → post mapping. Update whenever a new post is created.

- Next available SL#: 003
- 001 — "How to Find a Life Partner: A Trust-First Guide for Serious Matrimony" — `drafts/en/001-how-to-find-a-life-partner-trust-first-guide-2026-08-05.md` (en) and `drafts/bn/001-how-to-find-a-life-partner-trust-first-guide-2026-08-05-bn.md` (bn) — **Published** (2026-08-14)
- 002 — "How to Help Your Son or Daughter Find a Life Partner (Without Taking Over)" — `drafts/en/002-how-parents-can-help-find-a-life-partner-2026-08-14.md` (en) — **Publish-ready** (fact-checked and independently reviewed, 2026-08-14). Bengali version not yet started. Before publish: re-confirm the 5 Related Posts/internal-link slugs against the live sitemap (network egress was blocked in this session, so they were reused from article #1's own links rather than freshly verified).

## Recent Progress

- Explored https://connect.panosia.com (homepage, sitemap, key posts, pricing, about page).
- User confirmed first-pass assumptions ("mostly good").
- Corrected pricing model: free forever, no subscriptions; optional one-time verification services are the only paid products.
- Added founder context from about page: founded Nov 2025 in North Carolina, mission/vision, values (Integrity, Respect, Connection), brand pillars, and "LinkedIn of matrimony" ambition.
- User chose to skip external research data for now.
- First article topic agreed: "How to Find a Life Partner: A Trust-First Guide for Serious Matrimony" (hub-style, ties into existing how-it-works post), targeted at Candidates only.
- Content strategy: role-based series for Candidate, parents/family, volunteer matchmakers, and local professional matchmakers (recorded in user-notes.md).
- First article drafted: drafts/en/001-how-to-find-a-life-partner-trust-first-guide-2026-08-05.md (SL# 001; filed under the original date-stamped name at the time, since moved into the SL#/language-subfolder convention). Fact-checked and independently reviewed; publish-ready with only optional polish remaining. Required fixes incorporated: FTC romance-scam link corrected, background-check wording aligned to pricing page, verification mechanics updated to the new self-service flow (launch post linked).
- Second revision round (2026-08-06): rewrote the intro with a stronger hook ("Finding a Life Partner Starts With Trust"), added a "When Family Is Spread Across Countries" section, added a required FAQ section, reframed the Ryan persona as explicitly hypothetical, and re-ran fact-check + independent review. Required fixes incorporated: removed invented time/speed claims, softened an unverified cross-border access claim, reduced duplicated privacy-controls wording across three sections, smoothed two keyword-forced sentences. Verdict: publish after required fixes — fixes applied, draft is publish-ready.
- New durable writing standards recorded in context/user-notes.md and docs/article-writing.md (2026-08-06): every intro needs a hook; write for a broad/diverse readership (native and non-native, younger and older readers); always include a short FAQ section; follow "less is more"; actively check for and reduce duplication across sections. Apply these to all future articles, including the parent/family guide.

- Article #1 (Candidate guide) marked published (2026-08-14).
- Article #2 (parent/family guide) drafted, fact-checked, and independently reviewed (2026-08-14). Verdict: publish-ready. Core thesis (user-provided): parents already run an informal trusted network (friends, colleagues, siblings/cousins, religious gatherings, an Imam/religious leader, professional matchmakers); Panosia Connect gathers that same network onto one platform via the Connector role, the way LinkedIn/Facebook did for their categories; vouching works both ways; the shared network compounds so helping your own child positions a parent to help others too.
- Global-readability pass on article #2 (2026-08-14): fixed two ambiguous comma-list sentences, replaced idioms ("who-knows-who," "work the phone," "cold profile," "go cold") with plain language, replaced finance jargon ("the network compounds") with a plainer phrase, split one overloaded sentence, and grounded the LinkedIn analogy on its first body mention. Surgical wording-only changes; thesis, structure, facts, FAQ, Related Posts, and frontmatter untouched. Draft remains publish-ready.
- New workflow preference recorded (2026-08-14): before writing a full draft, show a paragraph-by-paragraph outline for user review and approval first; wait for sign-off before drafting full prose. Apply to article #3 onward.
- Added `/hv-article-review` skill (`.claude/skills/hv-article-review/SKILL.md`, 2026-08-14): multi-persona review (native English, diaspora/immigrant, young, divorced mid-age, unfamiliar-with-platform, industry-editor readers, plus supporting lenses). Ran it on article #2 and applied the required fixes: defined "Candidate" on first use in Getting Started, rewrote the Meta Description so its first sentence lands at the 200-char feed-card truncation point instead of cutting mid-word, trimmed a duplicated "this is normal" beat across two sections, and aligned the Primary Keyword frontmatter field to the natural phrasing actually used. Article #2 remains publish-ready.

## Next Recommended Step

- Article #2 is publish-ready pending a live-sitemap re-check of its 5 internal links (see Content Index note). After that: publish article #2, start the Bengali version of article #1 or #2, or move to article #3 (volunteer matchmaker guide) in the role-based series.
