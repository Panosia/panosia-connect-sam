---
name: hv-content-planning
description: Manually-triggered content planning pass — checks current SEO performance, runs the relevant OpenSEO research skills (keyword research, competitive landscape, competitor analysis, keyword clustering, link prospecting), tops up the Notion Blog Posts DB content queue with new Idea rows, and documents findings/reasoning in a Marketing Campaigns page. Use when the user invokes /hv-content-planning or asks to plan next month's content, refresh the content queue, or run a content planning pass.
---

This is the human-triggered counterpart to the "Daily Blog Draft" cloud routine. That routine only drains the Notion Blog Posts DB queue (`Status = Idea`/`Research`, ordered by `Priority`); it cannot run OpenSEO research (cloud routines don't have that connector). This skill is how the queue gets refilled — run it whenever you decide it's time, there's no fixed schedule. Everything it produces goes into Notion, since Notion (not this repo's `MEMORY.md`) is now the source of truth for what to write next.

## Usage

`/hv-content-planning [--skip-research] [--month "<Month Year>"]`

- No flags → full pass: check queue health, check performance, run research as needed, top up the queue, write the campaign page.
- `--skip-research` → only do the queue-health and campaign-page-write steps, skip all OpenSEO research calls (useful for a quick status pass, or when credits are tight).
- `--month` → defaults to next calendar month if not given (e.g. run in late September plans "October 2026").

## Step 1: Check queue health first

Query the Notion "Blog Posts" data source (`collection://10fb6499-cacb-4b31-8e1c-c74246331923`) for rows where `Status IN ('Idea', 'Research')`, ordered by `Priority`. Report: how many rows are pending, the oldest one's age, and whether `Priority` values have gaps or ties worth cleaning up.

If there are already 5+ healthy pending rows and the user didn't force a run, say so and ask whether to proceed with more research anyway (avoid spending credits to pad an already-adequate queue) — skip straight to Step 5 if they'd rather not.

## Step 2: Free performance check (no credits)

Pull `get_search_console_performance` (dimensions `["page"]`, `last_3_months` or similar) for the OpenSEO project. Identify:
- Striking-distance pages (position 3-15, low CTR) — candidates for a refresh/rewrite rather than new content.
- Which existing published posts (cross-reference Blog Posts DB rows with `Status = Published`) are underperforming their keyword's real demand.

This context should influence prioritization in Step 4, not just add new topics blindly.

## Step 3: Run the relevant OpenSEO research skills

Not all five every time — pick based on what's actually missing, and confirm with the user before any call likely to spend meaningful credits (each underlying skill already has its own credit-confirmation guardrail; respect it):

- **`keyword-research`** — when a persona/market bucket has no fresh keyword data, or existing data is over ~30 days old (check the OpenSEO project's research log first via `get_project_context` to avoid re-buying recent research).
- **`competitive-landscape`** — when entering a market/persona bucket not yet mapped, before picking specific competitors.
- **`competitor-analysis`** — to go deep on one competitor that `competitive-landscape` or prior research flagged as important. Findings append to that competitor's row (Notes) in the Notion Market Competitors DB (search for it if not already in context).
- **`keyword-clustering`** — run on the accumulated raw keyword findings (fresh from this pass, or already-logged ones if `--skip-research` isn't set but nothing new came up) to group them into page-level topic clusters. **This is the step that directly produces new content ideas** — treat its output as the candidate list for Step 4.
- **`link-prospecting`** — only when a specific published post is a strong linkable asset ready for outreach (ask the user which post, if any, before running this — it's about promotion, not new content ideas, so don't run it by default).

## Step 4: Turn clusters into queued content

For each keyword cluster worth drafting (confirm the shortlist with the user rather than queuing everything blindly):

1. Check `SELECT MAX("SL#") FROM` the Blog Posts data source to avoid SL# collisions — new rows don't get an SL# yet (that's assigned at drafting time by the daily routine), so leave SL# blank on these.
2. Create a new page in the Blog Posts data source with:
   - `Title` — a working title for the piece.
   - `Status` — `Idea`.
   - `Persona` — one of `Serious Candidate` / `Connector/Matchmaker` / `Protective Parent/Family` / `Community-Minded Leader`.
   - `Primary Keyword` — the cluster's anchor keyword.
   - `Priority` — a number continuing from the current highest pending priority, ordered by real business value (search volume, competitive gap size, how directly it maps to a Panosia feature) — not just discovery order.
   - `Folder Path` — a proposed `posts/<slug>/` path (SL# comes later).
   - Body: a `## Research Brief` section (mirror the shape of existing rows — primary/secondary keywords, real demand numbers with source and date, core thesis, reader/persona fit, angle, what to avoid/overlap with existing posts).
3. Never duplicate a topic that's already queued or published — check existing Blog Posts DB titles/keywords first.

## Step 5: Write the campaign page

Create or update a page titled `SEO & AEO Content Campaign - <Month Year>` in the `📣 Marketing Campaigns` data source (`collection://f8bb78ed-118c-4198-90e3-e891e5a9ac3a`, database page `https://app.notion.com/p/11566cc3489e4925a5e15fd40e32c843`):

- Properties: `Campaign` (title), `Start date`/`End date` (the target month), `Status` = `Planned`, `Primary KPI` = `Signups` (matches the north-star goal), `Audience` (relation to the relevant Buyer Personas rows this month's queue targets, if the relation is quick to set — otherwise note personas in the body).
- Body: what changed this pass (queue health before/after, performance findings from Step 2, research findings from Step 3 with sources/dates, the reasoning behind this month's priority order), and what's now queued (link each new Blog Posts DB row).
- If Step 1 found the queue was already healthy and no research ran, still write a short entry noting that this month's plan is "carried over, no changes" rather than skipping the campaign page entirely — keeps the Marketing Campaigns DB an honest monthly record.

## Step 6: Report back

Plain summary: queue health before/after, credits spent (and on what), how many new Idea rows were added, and the campaign page link. Flag anything you're unsure about (a cluster that might overlap an existing post, a persona assignment you're not confident in) rather than silently guessing.

## Guardrails

- Never invent search volume, competitor data, or performance numbers — every figure in a Research Brief or the campaign page must trace back to an actual OpenSEO tool result or GSC data, with the date it was pulled.
- Never set a Blog Posts DB row's `Status` past `Idea` here — that transition (`Drafting` → ... → `Publish-Ready`) belongs to the daily drafting routine, not this planning pass.
- Respect each underlying OpenSEO skill's own credit-confirmation behavior; don't chain multiple paid calls without the user's awareness of the running total.
- If OpenSEO MCP tools aren't available in the current session, say so plainly and stop rather than proceeding on stale assumptions (same rule as the rest of this project's OpenSEO-dependent workflows).
