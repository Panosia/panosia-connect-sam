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

- 001 — "How to Find a Life Partner: A Trust-First Guide for Serious Matrimony" — `posts/001-how-to-find-a-life-partner-trust-first-guide/` — en (`001-article.md`), bn (`001-article.md`), social posts (all posted) — **Published** 2026-08-14
- 002 — "How to Help Your Son or Daughter Find a Life Partner (Without Taking Over)" — `posts/002-how-parents-can-help-find-a-life-partner/` — en (`002-article.md`), bn (`002-article.md`), research.md — **Publish-ready** (en and bn); social posts drafted 2026-09-06 for Facebook/LinkedIn/X, en (`en/002-social-posts.md`) and bn (`bn/002-social-posts.md`); links flagged not-live pending publish. Verification framing corrected 2026-09-06 in both languages — states the honest split: free for Connector/reference/profile-sharing, Level 1 required before the Candidate can search/Discover/request Private View/chat. External editorial review (2026-09-06): opening rewritten to lead with a hook before the Farida vignette instead of after; the 3 sections restating the network→scattered→one-place thesis compressed ~20-25% each; generalized Imam claim replaced with "a community leader making an introduction is putting their own credibility behind it too"; verification paragraph shortened; all 5 FAQ answers tightened; "How to Help Without Taking Over" and "Getting Started Together" left untouched per reviewer's note. `/hv-article-review` pass same day on the revised en caught 4 regressions the compression had introduced (an undefined "Discover" reference, a dropped "request Private View" item from the FAQ's verification-gate list, 4 comma splices, and "mosque, church, or temple" narrowed to "mosque" only) — all fixed. bn resynced via `bn-translator` same day against the fully-fixed en, with those same 3 content-level fixes (multi-faith phrasing, Discover gloss, Private View in FAQ) manually re-applied since the agent had started from an intermediate en version. **Internal links not re-verified against the live sitemap this round** — last confirmed live 2026-08-26; re-check before publishing given time elapsed. En updated again 2026-09-09 (Farida vignette reworded to drop "hypothetical," two inline images added, verification paragraph cut from the "Building Trust Through References" body since FAQ already covers it); bn resynced same day via `bn-translator` to match, including a leftover compression (colleague/nephew line) it caught from the earlier 2026-09-06 sync that had been missed.
- 003 — "Volunteer/Community Matchmaker Guide" (working title) — `posts/003-volunteer-matchmaker-guide/` — research.md only, not drafted; next in the role-based series
- 004 — en title "Getting Started on Panosia Connect: Build Trust and Get Discovered", bn title diverged intentionally: "Panosia Connect-এ কীভাবে বিশ্বাস যোগ্য প্রোফাইল তৈরি করবেন এবং সফল হবেন" (see bn-title-can-diverge-from-en note below) — `posts/004-getting-started-on-panosia-connect/` — en (`004-article.md`, `004-social-posts.md` for FB/IG/LinkedIn/X), bn (`004-article.md`, retranslated 2026-08-26) — **Publish-ready** (en); rewrite of an already-live page at the same URL, publishing overwrites live content, confirm before pushing. Step order is now: 1 Profile, 2 Privacy, 3 Trust Network, 4 Get Verified, 5 Share and Get Discovered, 6 Message, 7 Involve Family (verification moved earlier, ahead of share/message, since it gates them, see verification fact below). 9 images hotlinked from the live site rather than copied into `images/` (nonstandard vs. `docs/image-workflow.md`, revisit if local copies wanted). bn draft fully re-translated to match this structure and the verification correction, its 4 in-body/related links point at live `/bn/` equivalents (the 5th, blur-your-profile-photo-for-public-viewers, has no bn version so stays English); social posts exist for en only so far. Sitemap check on 2026-09-06 (during article #2's `/hv-article-review` pass) found both en and bn versions of this URL already live on-site (`https://connect.panosia.com/posts/getting-started-on-panosia-connect-build-trust-and-get-discovered` and its `/bn/` equivalent) — this MEMORY.md entry's "not yet published" status was stale. Reconcile this bundle's local drafts against what's actually live before treating either language as still pending.

## Future Topic Cluster Ideas (not yet SL#'d)

From external editorial feedback on article #2 (2026-09-06): Candidate-search and parent/family-search are genuinely separate search intents ("how to find a life partner" vs. "how can I help my son/daughter find a spouse") and should stay as separate articles, not merged — this matches the existing role-based series decision, not a change to it. The reviewer's suggested cluster around articles #1 and #2, to strengthen topical footprint:

- How to Find a Life Partner: A Trust-First Guide (= article #1, published)
- How to Help Your Daughter or Son Find a Life Partner (= article #2)
- What Is a Connector? (already exists as a live site page linked from #1/#2, not a `posts/` bundle — confirm whether it needs its own SL# bundle or stays a standalone site page)
- How Family References Build Trust in Matrimony (new topic idea)
- How to Involve Your Parents in Your Matrimonial Search (new topic idea — the Candidate-side mirror of article #2's parent-side angle)
- How Identity Verification Works in Matrimony (new topic idea)
- Questions to Ask Before Pursuing a Marriage Proposal (new topic idea)

None of these are drafted or SL#'d yet. Slot the new ones into the existing role-based series planning (`context/user-notes.md`) when picking the next article after #3 (volunteer matchmaker).

## Recent Progress (Milestones)

- Site research, company/audience/pricing/founder facts confirmed with user (2026-08-05).
- Content strategy: role-based series, Candidate → parents/family → volunteer matchmaker → professional matchmaker, one audience per article (`context/user-notes.md`).
- File convention (2026-08-15): one page-bundle folder per post, per-language subfolders, dates in frontmatter not filenames, see `AGENTS.md` for the full spec.
- File naming settled (2026-08-26, user decision, after trying and then reverting a folder-level change): bundle **folder** keeps the topic slug as before, `posts/<SL#>-<topic-slug>/`, e.g. `posts/004-getting-started-on-panosia-connect/`. Per-language files that carry real content dropped their generic names for SL#-prefixed ones: `<lang>/<SL#>-article.md` (e.g. `en/004-article.md` not `en/article.md`) and `<lang>/<SL#>-social-posts.md` (e.g. `en/001-social-posts.md` not `en/social-posts.md`). `research.md` keeps its plain generic name, unaffected (it's shared across languages, one per bundle, no ambiguity). Reason: a per-language file needs its own identifier since it can end up opened outside its folder context (e.g. shared standalone), the folder's topic slug already makes the bundle identifiable on its own. Renamed all existing files to match (article: 001, 002, 004, 003 has none yet; social-posts: 001 only, the sole post with social copy so far); updated `AGENTS.md`, `docs/article-writing.md`, `docs/image-workflow.md`, README, both skills, and all agent files (`.claude/agents/`, `.opencode/agents/`), including in-content cross-references (article #1's bn translation and social-posts source line). Article URLs/slugs (the actual published `/posts/<slug>` path) are unaffected, this is only local file naming.
- Writing standards accumulated in `context/user-notes.md` / `docs/article-writing.md`: intro hook, broad-readership plain language, required FAQ, less-is-more, no em dash as default, meta-description-as-hook format, don't presume the reader's personal history via "you" (2026-08-26).
- `/hv-article-review` (multi-persona) and `/hv-social-content` skills added 2026-08-14/15.
- `context/site-profile.md` carries a detailed "Product Features" section sourced from the live app's homepage (sibling repo `panosia-connect`); refreshed 2026-08-26 after a landing-page update. Re-verify against that source before trusting product-mechanic claims, the homepage gets restructured often; `site-profile.md` itself flags known-removed sections.
- Article #4 migrated from a stray untracked `posts/getting.md` into the bundle convention and fully rewritten, fact-checked, and reviewed (2026-08-26).
- Vocabulary decision (2026-08-26): "reference"/"be a reference for" replaces "vouch"/"vouching" as the preferred term (`context/brand-voice.md`), it's the app's own current term (`Verification References`, `Be a Reference`) and more globally familiar to non-native readers. Applied throughout article #2's en draft. Still present in article #1 (published) and article #4 (unpublished draft) and 2 `research.md` files, not yet updated there, pending a decision on whether/how to touch the published one.
- Article #2's bn translation drafted via `bn-translator` (2026-08-26): established বn renderings for "reference" (রেফারেন্স) and "professional matchmaker" (পেশাদার ঘটক), and confirmed "Panosia Connect" stays plain English in bn body text (matches article #1's published precedent, no bilingual gloss) — see `context/user-notes.md`'s bn terminology note.
- Verification-requirement product fact corrected (2026-08-26, confirmed by user): Level 1 ID Verification is NOT required to create a profile, use Profile Import, control privacy, share a profile (Public/Private View), or export to PDF, all of that is free and ungated. It IS required before any interaction with other users: search, Discover, requesting someone's Private View, or chat. Updated `context/site-profile.md`'s verification bullet and `context/brand-voice.md`'s "terms to avoid" and messaging-priorities caveats (previously said never call verification "required," now states the honest split). Applied throughout article #4 (en restructured, bn re-translated to match) and article #2 (en+bn, fixed 2026-09-06); article #1 (published) still has the old "never required" framing, not yet updated pending a decision on touching the live published post.
- bn titles can diverge from en when there's an audience-specific reason, not a 1:1 translation requirement (2026-08-26 decision): article #4's bn title dropped a "getting noticed" framing (নজরে আসা) that read as too forward for a conservative bn readership, landing on a "trustworthy profile + succeed" framing instead, while en kept its original "Build Trust and Get Discovered." Article #1 remains the precedent for when titles *should* stay parallel (no audience-specific reason to diverge there).

## Notion Sync

- Set up 2026-09-11: a "Blog Posts" Notion database (already existed from an earlier session, under Panosia Connect's Marketing & Sales teamspace) is now tracked in `.notion-sync-state.json` (gitignored, local sync cache) and kept in sync via the `hv-notion-sync` skill (`/hv-notion-sync`). A companion "🧭 Sam Workspace Memory" hub (7 pages: Memory & Status, Editorial Workflow & Rules, Brand Voice, Site Profile, User Notes, Writing & Review Standards, SEO Guidelines & Keywords) mirrors this repo's own context files one-way (repo → Notion only) so other AI sessions without repo access (Cowork, Claude Desktop, other connected agents) have the same grounding. The repo stays the actual source of truth for both; re-run `/hv-notion-sync` after meaningful repo changes to refresh Notion, it does not auto-update. Article #4's bn article body was pushed in full during this setup (previously a placeholder in Notion).

## Next Recommended Step

- Article #2 (en and bn) is publish-ready; re-verify its internal links against the live sitemap before pushing (last checked 2026-08-26). Article #4 is publish-ready but overwrites a currently-live page, worth a deliberate go/no-go before pushing. Otherwise: finish article #4's bn translation (in progress), move to article #3, or pick a next topic from the new Future Topic Cluster Ideas list.
