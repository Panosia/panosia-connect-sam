# Sam Memory

This file tracks setup state and working assumptions so new sessions can orient quickly. It's loaded into every session via `CLAUDE.md`, keep entries short and current. Durable writing rules belong in `context/user-notes.md` / `docs/article-writing.md`; detailed product facts belong in `context/site-profile.md`. Point to those files instead of restating their content here.

## Onboarding Status

- Status: Good enough (2026-08-05). Done: company basics, audience/content goals, brand voice, starter keywords. Research-data integration (DataForSEO) declined for now, can revisit.
- Optional, deferred: internal links map.

## Current Known Context

- Company: Panosia Connect (Panosia LLC) — https://connect.panosia.com
- Product: trust-based marriage/matchmaking platform; Candidate (searching) and Connector (vouches/facilitates) roles
- Offer: free-to-join, no subscriptions; only paid products are optional one-time verification services
- Audience: Candidates + Connectors (family/community introducers); English + Bengali markets
- Content goal: organic acquisition for matrimony/trust queries → signup, network growth, optional verification

## Gaps To Resolve

- Internal links map: optional, can be deferred.
- Keyword map: first pass only; refine with real search data later if desired.

## Content Index (SL#)

Next available SL#: 005

- 001 — "How to Find a Life Partner: A Trust-First Guide for Serious Matrimony" — `posts/001-how-to-find-a-life-partner-trust-first-guide/` — en, bn, social posts (all posted) — **Published** 2026-08-14
- 002 — "How to Help Your Son or Daughter Find a Life Partner (Without Taking Over)" — `posts/002-how-parents-can-help-find-a-life-partner/` — en, research.md — **Publish-ready**; internal links verified live against sitemap 2026-08-26; no bn/social yet
- 003 — "Volunteer/Community Matchmaker Guide" (working title) — `posts/003-volunteer-matchmaker-guide/` — research.md only, not drafted; next in the role-based series
- 004 — "Getting Started on Panosia Connect: Build Trust and Get Discovered" — `posts/004-getting-started-on-panosia-connect/` — en only — **Publish-ready**; rewrite of an already-live page at the same URL, publishing overwrites live content, confirm before pushing; images hotlinked from the live site rather than copied into `images/` (nonstandard vs. `docs/image-workflow.md`, revisit if local copies wanted); no bn/social yet

## Recent Progress (Milestones)

- Site research, company/audience/pricing/founder facts confirmed with user (2026-08-05).
- Content strategy: role-based series, Candidate → parents/family → volunteer matchmaker → professional matchmaker, one audience per article (`context/user-notes.md`).
- File convention (2026-08-15): `posts/<SL#>-<slug>/` bundles, per-language subfolders, dates in frontmatter not filenames, see `AGENTS.md` for the full spec.
- Writing standards accumulated in `context/user-notes.md` / `docs/article-writing.md`: intro hook, broad-readership plain language, required FAQ, less-is-more, no em dash as default, meta-description-as-hook format, don't presume the reader's personal history via "you" (2026-08-26).
- `/hv-article-review` (multi-persona) and `/hv-social-content` skills added 2026-08-14/15.
- `context/site-profile.md` carries a detailed "Product Features" section sourced from the live app's homepage (sibling repo `panosia-connect`); refreshed 2026-08-26 after a landing-page update. Re-verify against that source before trusting product-mechanic claims, the homepage gets restructured often; `site-profile.md` itself flags known-removed sections.
- Article #4 migrated from a stray untracked `posts/getting.md` into the bundle convention and fully rewritten, fact-checked, and reviewed (2026-08-26).

## Next Recommended Step

- Article #4 is publish-ready but overwrites a currently-live page, worth a deliberate go/no-go before pushing. Article #2 is also fully publish-ready. Otherwise: start a Bengali version of article #1, #2, or #4, or move to article #3.
