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
- File organization (2026-08-15, supersedes the 2026-08-07 flat `drafts/`/`research/`/`social/` convention): every post is one page-bundle folder, `posts/<SL#>-<topic-slug>/` — **no date in the folder name**. Inside: `research.md` (optional brief), `<lang>/article.md` per language including English (`en/`, `bn/`), `<lang>/social-posts.md` once social copy exists (sectioned by platform), and a shared `images/` folder created on first use (see `docs/image-workflow.md`). The SL#/slug live once on the folder, not repeated on every file inside it. `drafts/`, `research/`, `social/`, and the never-used `published/` folders are retired; all three existing articles were migrated on 2026-08-15 (see Content Index for new paths).
- Dates moved from filenames into frontmatter (2026-08-15): each language's `article.md` now carries its own `Draft Date` and `Publish Date` fields (see `templates/article-frontmatter.md`), instead of one date baked into the old dated filename/folder. This is per-language on purpose, a translation is drafted and published on its own timeline, not the English source's; `bn-translator` sets its own dates rather than copying the English source's.

## Content Index (SL#)

Tracks the next available serial number and the SL# → post mapping. Update whenever a new post is created.

- Next available SL#: 004
- 001 — "How to Find a Life Partner: A Trust-First Guide for Serious Matrimony" — `posts/001-how-to-find-a-life-partner-trust-first-guide/` — `en/article.md`, `bn/article.md`, `en/social-posts.md` (Facebook/LinkedIn/X copy drafted and posted 2026-08-15) — **Published** (2026-08-14)
- 002 — "How to Help Your Son or Daughter Find a Life Partner (Without Taking Over)" — `posts/002-how-parents-can-help-find-a-life-partner/` — `en/article.md`, `research.md` — **Publish-ready** (fact-checked and independently reviewed, 2026-08-14; multi-persona `/hv-article-review` pass 2026-08-26 confirmed no product-fact drift against the refreshed homepage context and applied light wording fixes, see Recent Progress). All 5 Related Posts/internal-link slugs (plus the in-body link to article #1) reconfirmed live against `sitemap-posts.xml` on 2026-08-26, the prior pending verification is resolved. Bengali version not yet started; no social copy yet.
- 003 — "Volunteer/Community Matchmaker Guide" (working title) — `posts/003-volunteer-matchmaker-guide/` — `research.md` only. Draft not yet started; next in the role-based series.

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
- Added `/hv-article-review` skill (`.claude/skills/hv-article-review/SKILL.md`, 2026-08-14): multi-persona review (native English, diaspora/immigrant, young, divorced mid-age, unfamiliar-with-platform, industry-editor readers, plus supporting lenses). Ran it on article #2 and applied the required fixes: defined "Candidate" on first use in Getting Started, rewrote the Meta Description so its first sentence lands at the 200-char feed-card truncation point instead of cutting mid-word, trimmed a duplicated "this is normal" beat across two sections, and aligned the Primary Keyword frontmatter field to the natural phrasing actually used.
- New output type (2026-08-15): social media post copy. Added `/hv-social-content` skill (`.claude/skills/hv-social-content/SKILL.md`) to convert a blog/article draft into platform-native social copy: picks the sharpest angle, applies per-platform mechanics (hook window, link-in-first-comment vs. native link, hashtag counts, tone), and enforces brand-voice guardrails (no new claims beyond the source article, no hype/urgency, correct product terms, one CTA). Always asks which platform(s) (Facebook pre-selected as default) unless the user already named one. First run: 3 platforms (Facebook, LinkedIn, X) for article #001, saved to `posts/001-.../en/social-posts.md` (see Content Index).
- Restructured file organization to page bundles (2026-08-15, see the Gaps To Resolve note above for the full convention): moved articles 001–003 from `drafts/`/`research/`/`social/` into `posts/<SL#>-slug-date>/`, merged the 3 separate per-platform social files for article #001 into one sectioned `social-posts.md`, and retired the unused `published/` folder. Updated `AGENTS.md`, `docs/article-writing.md`, `templates/article-frontmatter.md`, both skills, and the `article-writer`/`fact-checker`/`bn-translator`/`seo-guide` agent definitions in both `.claude/agents/` and `.opencode/agents/` to match. Also scoped a real image workflow (`docs/image-workflow.md`): `images/` folder per bundle, `hero.<ext>`/`image-N.<ext>` naming, alt text inline in the article body (or in new optional `Hero Image`/`Hero Image Alt` frontmatter fields for the hero image), and an `images/sources.md` licensing log created on first image use. No images exist yet for any article; this is groundwork, not yet exercised.
- Author's-judgment pass on the optional polish (2026-08-14): applied the ones that clearly improved the piece — added one inclusive clause covering readers helping with a second marriage, cut a repeated "gap" wording, simplified "positioned to help others" to plainer language, split two dense paragraphs for scannability, and tightened the first FAQ answer so it adds rather than restates. Skipped two optional suggestions on purpose: leaving the Imam-first sentence as-is (already softened by "or another local religious leader"; making it a list would trade concreteness for box-checking), and not adding a scam/accountability sentence (article #1 already owns that territory in depth; adding it here would duplicate scope). Article #2 remains publish-ready.

- All 3 social posts for article #1 (Facebook, LinkedIn, X) marked posted 2026-08-15 in `posts/001-.../en/social-posts.md` (`Status` field on each, flipped by hand per the user's confirmation, not verified against the live platforms by Sam).
- Added a detailed "Product Features" section to `context/site-profile.md` (2026-08-26), extracted from the live app's homepage (`panosia-connect/src/pages/HomePage.tsx` + `src/i18n/locales/en/home.json`, a sibling repo). Covers profile import/export, Public/Private multi-view, field-level privacy, Discover filters, shareable links, Managed Profiles, the 3-tier verification ladder (Level 1 ID / Level 2 Background Check / Level 3 In-Person, plus credit/criminal history checks marked "coming soon," not live), Verification References, Family Tree, Social Connections, the Connector role and its personas, privacy/safety controls, Secure Chat, and pricing. Use it for feature-accurate detail in future drafts instead of guessing at mechanics.
- Refreshed that same "Product Features" section (2026-08-26, same day) after the user pulled a newer `panosia-connect` commit (`92fc716a`, "update landing page," 2026-08-24). That commit trimmed/restructured the homepage: Connector personas consolidated 6→3, Connector capabilities reorganized into a 4-card "what you can do" set plus a separate 2-card own-privacy reassurance pairing, the Old Way/Panosia Connect Way comparison cut from 4 rows to 2, the dedicated Discover/search section and the "How It Works" video section removed, the Trust & Transparency section (bank-grade/GDPR/Report/Block/Pause/Delete) removed (Report/Block no longer appear anywhere on the homepage), About Us cut down to just title + one line + founding date, the pricing money-back guarantee line dropped, and the blog teaser trimmed from 6 posts to 3. `site-profile.md` now flags each removed/changed item explicitly so future drafts don't cite stale homepage messaging.
- Ran `/hv-article-review` on article #2 (2026-08-26): re-verified all 5 Related Posts slugs plus the in-body article #1 link against a fresh `sitemap-posts.xml` fetch, all live; cross-checked its product claims (Connector role, vouching, optional one-time verification) against the just-refreshed Product Features context, no drift found. Verdict: publish after required fixes, fixes were light wording only. Applied: split an overlong LinkedIn/Facebook-analogy paragraph in two for scannability, and trimmed three near-identical repeats of a "the same [thing] you already do informally" phrasing pattern (in "Your role in this doesn't change," the vouching-instinct line, and the Getting Started Connector-join line) to remove the stylistic tic without losing meaning. Skipped as not worth taking: the script's "no internal links found" and "keyword missing from meta description" warnings (both expected given this project's absolute-URL link format and the hook-style meta description house rule), and splitting the "your network is scattered" list paragraph (reads fine as one tight unit). Structure, thesis, FAQ, and Related Posts untouched. Article #2 remains publish-ready.

## Next Recommended Step

- Article #2 is fully publish-ready, no remaining blockers. Publish it, start the Bengali version of article #1 or #2, or move to article #3 (volunteer matchmaker guide) in the role-based series.
