---
name: hv-content-planning
description: Manually-triggered content planning pass — reverse-engineers real keywords from known competitors (not blind seed-guessing), stages findings in a dedicated Notion Keyword Opportunities DB, runs the relevant OpenSEO research skills, tops up the Notion Blog Posts DB content queue with new keyword-backed Idea rows, and documents findings/reasoning in a Marketing Campaigns page. Use when the user invokes /hv-content-planning or asks to plan next month's content, refresh the content queue, run a content planning pass, or reach a target number of queued posts.
---

This is the human-triggered counterpart to the "Daily Blog Draft" cloud routine (`trig_01XgCYnVnZCdtBng2hBEReth`, runs daily 8am ET). That routine only drains the Notion Blog Posts DB queue (`Status IN ('Idea','Research')`, ordered by `Priority`); it cannot run OpenSEO research (cloud routines only have the Notion connector, not OpenSEO). This skill is how the queue gets refilled — run it whenever the user decides it's time, there's no fixed schedule. Everything it produces goes into Notion, since Notion (not this repo's `MEMORY.md`) is the source of truth for what to write next. `MEMORY.md`'s "Automated Content Queue" section is fallback-only documentation.

## Notion data sources (exact IDs — don't re-derive these by searching each run)

| DB | Data source ID | Notes |
|---|---|---|
| **Blog Posts** | `collection://10fb6499-cacb-4b31-8e1c-c74246331923` | Properties: Title, Status (Idea/Research/Drafting/Fact-Check/Review/Publish-Ready/Published), Persona (select: `Serious Candidate`/`Connector/Matchmaker`/`Protective Parent/Family`/`Community-Minded Leader`), Priority (number), SL# (number, leave blank on new Idea rows — assigned at drafting time), Primary Keyword, Slug, Folder Path, Draft Date, Publish Date, Live URL, Social Posted. Parent page: `https://app.notion.com/p/3d3cf9080bd680b78455f86ee7251083` ("Blog"). |
| **Keyword Opportunities** | `collection://d4683c66-7907-4c8e-9efe-57e8f3da464a` | Staging table, created 2026-09-12. Properties: Keyword (title), Search Volume, Location/Language (text, e.g. "Bangladesh/bn" vs "US/en"), Persona (same 4-value select as Blog Posts), Source Competitor (two-way relation to Market Competitors), Status (`Raw`/`Clustered`/`Queued`/`Rejected`), Discovered Date, Notes. This is the input `keyword-clustering` reads from and the output `keyword-research`/`competitor-analysis`/`competitive-landscape` write to — always land findings here before deciding what becomes a Blog Posts row, don't skip straight to creating Idea rows from raw tool output. |
| **Market Competitors** | `collection://95971d9f-97d5-4787-a3bf-931227b94de6` | Properties: Name, Domain, Category (select: Matrimony Platform/Dating App/Biodata Tool/Individual Matchmaker), Persona (multi-select, 5 values matching the 5 researched persona buckets — note this is a *different* 5-value set than Blog Posts' 4-value Persona: `Muslim Candidates`/`Bangladeshi Diaspora`/`Diaspora Professional`/`Parents/Family`/`Professional Matchmakers`), Organic Traffic (Est. Monthly), Organic Keywords, Best Position, Notes. 44+ domains tracked as of 2026-09-12. |
| **📣 Marketing Campaigns** | `collection://f8bb78ed-118c-4198-90e3-e891e5a9ac3a` | Database page `https://app.notion.com/p/11566cc3489e4925a5e15fd40e32c843`. This is the *linked* one (has relations to Buyer Personas + Marketing Channels) — there is a second, unrelated "Marketing Campaigns" DB (`collection://62eb3d2e-...`) in the workspace; don't use that one. |
| **Buyer Personas** | `collection://0d90459a-410c-4450-b281-314b3cdaf654` | 15 personas in 4 priority buckets (see overview page `https://app.notion.com/p/3d6cf9080bd681caab40e7a61047c802`). Only 5 of the 15 have been keyword-researched so far (see "Persona coverage" below) — a real source of untapped topics. |
| OpenSEO project | `72341feb-0623-4bd3-8953-4f50e4a0896d` | Default market: US/English (locationCode 2840). Override to Bangladesh (locationCode `2050`, languageCode `bn`) for anything Bangladesh/Bengali-market — see the location lesson below. |

## Usage

`/hv-content-planning [--skip-research] [--month "<Month Year>"] [--target-count N]`

- No flags → full pass: check queue health, check performance, run research as needed, top up the queue, write the campaign page.
- `--skip-research` → only do the queue-health and campaign-page-write steps, skip all OpenSEO research calls (useful for a quick status pass, or when credits are tight).
- `--month` → defaults to next calendar month if not given (e.g. run in late September plans "October 2026").
- `--target-count N` → keep researching/clustering until the Blog Posts DB has at least N pending (`Idea`/`Research`) rows total, not just "some new ones" — useful for "give me a full month of posts" asks. Work through untapped persona buckets (see below) in priority order until the target is hit; don't pad with weak/low-fit clusters just to hit the number, say so if a genuine target can't be reached with real data.

## Step 1: Check queue health first

Query the Blog Posts data source for rows where `Status IN ('Idea', 'Research')`, ordered by `Priority`. Report: how many rows are pending, the oldest one's age, whether `Priority` values have gaps or ties worth cleaning up, and **which persona buckets are already represented** vs. thin/absent.

If there are already 5+ healthy pending rows and no `--target-count` was given and the user didn't force a run, say so and ask whether to proceed with more research anyway (avoid spending credits to pad an already-adequate queue) — skip straight to Step 6 if they'd rather not. Skip this check entirely when `--target-count` is given and the queue is below target.

## Persona coverage (know what's untapped before choosing seeds)

As of 2026-09-12, real keyword/competitor research has only covered **5 of the 15 Buyer Personas**: Muslim Candidates, Bangladeshi Diaspora, Diaspora Professional, Parents/Family, Professional Matchmakers. **Untapped personas** (real content opportunity, not yet researched): Home-Country Candidate (Bangladesh/India/Pakistan, distinct from diaspora), Values-First Western Candidate, Divorced, Widow, Aged Candidate, Christian/Hindu/Sikh Candidates specifically (as opposed to the Muslim-heavy research so far), Everyday Connector, Community/Religious Leader, Religious Institution. When topping up the queue, prefer seeding these untapped buckets over further mining the same 5 — that's where the real gaps are, not the already-well-covered Muslim/Bangladeshi-diaspora/matchmaker space.

## Step 2: Free performance check (no credits)

Pull `get_search_console_performance` (dimensions `["page"]`, `last_3_months`) for the OpenSEO project — skip if the research log shows this ran within the last few days (same-session reuse). Identify:
- Striking-distance pages (position 3-15, low CTR) — candidates for a refresh/rewrite rather than new content.
- Which existing published posts are underperforming their keyword's real demand.

This context should influence prioritization in Step 5, not just add new topics blindly.

## Step 3: Reverse-engineer before guessing seeds

**This is the validated method for this project — don't skip to blind seed-keyword guessing.** Blind guessing (typing a made-up seed phrase straight into `research_keywords` or `find_serp_competitors`) has repeatedly returned empty or noisy results here. What works:

1. Start from a **known competitor** in the target persona bucket (check Market Competitors DB first; if the bucket has zero tracked competitors, that's itself a signal — do a light `competitive-landscape` pass first to find 1-2 anchor domains before going further).
2. Pull that competitor's real ranked keywords (`get_ranked_keywords` via `competitor-analysis`) to source real seed phrases, or run `research_keywords` seeded from a phrase that competitor's own content already targets.
3. Only fall back to a direct guessed seed when no anchor competitor exists for that bucket yet.

**Two contamination traps to watch for** (found 2026-09-12, cost real credits before being caught):
- Broad matchmaker-adjacent seeds ("matchmaking muslim", "professional matchmaker") can pull in unrelated entertainment content (a reality TV show, a movie) that dominates the "related keywords" results. Skim results for obviously off-topic clusters (episode names, cast, "where to watch") before trusting volume numbers.
- A seed can look irrelevant under the wrong location/language and be a huge opportunity under the right one. **Always try Bangladesh location (`2050`) + Bengali language (`bn`) for anything Bangladesh-market-adjacent** before concluding a domain or term has no real traffic — the gap between US/English and Bangladesh/Bengali numbers has been as large as 500x in this project's own research (e.g. Biyeta.com: 28/mo measured wrong vs. 14,029/mo real).

## Step 4: Run the relevant OpenSEO research skills

Confirm with the user before any call likely to spend meaningful credits (each underlying skill already has its own credit-confirmation guardrail; respect it). Typical order for topping up the queue, per the method above:

1. **`competitor-analysis`** on 1-4 known competitors in an under-researched persona bucket (`get_ranked_keywords`, filter results for business fit — reject entertainment/tangential noise, reject terms that only fit a competitor's business model, not Panosia's). Write findings into that competitor's Market Competitors page body, and stage any usable keywords as new `Raw` rows in Keyword Opportunities (with Location/Language, Persona, Source Competitor set).
2. **`competitive-landscape`** when a whole persona bucket has no tracked competitors yet, to find 1-2 anchors before step 1, or to validate/broaden an existing bucket's coverage (`find_serp_competitors` on a real keyword set).
3. **`keyword-research`** seeded from real phrases surfaced in steps 1-2 (not guessed cold), to expand the pool. Stage results as `Raw` rows in Keyword Opportunities.
4. **`keyword-clustering`** on the accumulated `Raw`/`Clustered` Keyword Opportunities rows — group into page-level topics, map each cluster to either an **existing** queued Blog Posts row (enrich its brief, don't duplicate) or a **new** Idea row. This is the step that actually produces Step 5's content list.
5. **`link-prospecting`** — only when a specific published post is a strong linkable asset ready for outreach (ask the user which post, if any; it's about promotion, not new content ideas, so don't run it by default).

## Step 5: Turn clusters into queued content

For each keyword cluster worth drafting (confirm the shortlist with the user rather than queuing everything blindly, unless `--target-count` was given and there's a real shortfall):

1. Check `SELECT MAX("SL#") FROM` the Blog Posts data source to avoid SL# collisions if you ever do assign one early — but by default leave `SL#` blank on new Idea rows, it's assigned at drafting time by the daily routine.
2. Create a new page in the Blog Posts data source with:
   - `Title` — a working title for the piece (can be in the target language, e.g. Bengali, if the cluster is bn-first).
   - `Status` — `Idea`.
   - `Persona` — one of `Serious Candidate` / `Connector/Matchmaker` / `Protective Parent/Family` / `Community-Minded Leader` (map from the finer Market Competitors 5-persona or Buyer Personas 15-persona granularity to this coarser 4-bucket scheme).
   - `Primary Keyword` — the cluster's anchor keyword.
   - `Priority` — a number continuing from the current highest pending priority, ordered by real business value (search volume, competitive gap size, how directly it maps to a Panosia feature) — not just discovery order.
   - `Folder Path` — a proposed `posts/<next-number>-<slug>/` path, sequential from the highest folder-path number already used (SL# itself still comes later at drafting time).
   - Body: a `## Research Brief` section (mirror the shape of existing rows — primary/secondary keywords with real volume numbers and source/date, core thesis, reader/persona fit, angle, what to avoid/overlap with existing posts, language to draft in).
3. Never duplicate a topic that's already queued or published — check existing Blog Posts DB titles/keywords first.
4. Update each Keyword Opportunities row's `Status` to `Queued` once it lands in a Blog Posts row (or `Clustered` if grouped but not yet turned into a full page, e.g. a single low-volume keyword not worth its own article — note it in `MEMORY.md`'s Future Topic Cluster Ideas instead of forcing a thin Idea row).
5. If a cluster is genuinely too thin to justify its own row even after grouping, don't pad the queue with it — say so in Step 7's report instead.

## Step 6: Write the campaign page

Create or update a page titled `SEO & AEO Content Campaign - <Month Year>` in the Marketing Campaigns data source:

- Properties: `Campaign` (title), `Start date`/`End date` (the target month), `Status` = `Planned`, `Primary KPI` = `Signups` (matches the north-star goal), `Audience` (relation to the relevant Buyer Personas rows this month's queue targets, if quick to set — otherwise note personas in the body).
- Body: what changed this pass (queue health before/after, performance findings from Step 2, research findings from Steps 3-4 with sources/dates, the reasoning behind this month's priority order), and what's now queued (link each new Blog Posts DB row).
- If Step 1 found the queue was already healthy and no research ran, still write a short entry noting that this month's plan is "carried over, no changes" rather than skipping the campaign page entirely — keeps the Marketing Campaigns DB an honest monthly record.

## Step 7: Report back

Plain summary: queue health before/after (persona-bucket breakdown, not just a count), credits spent (and on what), how many new Idea rows were added, and the campaign page link. Flag anything you're unsure about (a cluster that might overlap an existing post, a persona assignment you're not confident in, a `--target-count` that couldn't be fully reached with real data) rather than silently guessing or padding.

## Guardrails

- Never invent search volume, competitor data, or performance numbers — every figure in a Research Brief or the campaign page must trace back to an actual OpenSEO tool result or GSC data, with the date it was pulled.
- Never invent a topic to hit a target count — a shortfall reported honestly is better than a low-fit row padding the queue.
- Never set a Blog Posts DB row's `Status` past `Idea` here — that transition (`Drafting` → ... → `Publish-Ready`) belongs to the daily drafting routine, not this planning pass.
- Respect each underlying OpenSEO skill's own credit-confirmation behavior; don't chain multiple paid calls without the user's awareness of the running total.
- If OpenSEO MCP tools aren't available in the current session, say so plainly and stop rather than proceeding on stale assumptions (same rule as the rest of this project's OpenSEO-dependent workflows).
- Multi-page `notion-create-pages` calls with several long Bengali-script bodies have occasionally failed to parse or introduced stray combining-character glitches in this project — create pages in batches of 2-3 rather than one large batch, and spot-check non-Latin titles/keywords after creation.
