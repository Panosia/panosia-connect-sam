---
name: hv-notion-sync
description: Two-way sync between a Notion "Blog Posts" database and this repo's posts/ bundles — status, metadata, and full article content per language. Also one-way (repo → Notion) sync of the workspace-memory hub (MEMORY.md, AGENTS.md workflow rules, brand voice, site profile, user notes, writing/review standards, SEO guidelines) so other AI sessions without repo access (Cowork, Claude Desktop, other agents) can read current context from Notion. Use when the user invokes /hv-notion-sync or asks to sync, push, or pull blog posts or workspace memory to/from Notion.
---

Notion serves two related but separate purposes here, and this skill covers both:

1. **Blog Posts database** — a status dashboard and reviewable copy of every post; `posts/` on disk stays the place drafting actually happens. Two-way, per post per language.
2. **Sam Workspace Memory hub** — a read mirror of the repo's own context files (MEMORY.md, AGENTS.md, context/*.md, docs/*.md), for AI sessions that don't have repo access. One-way, repo → Notion only: the repo is always the source of truth here, Notion is never edited back into it.

## Usage

`/hv-notion-sync [--setup] [--push|--pull] [<SL#>] [--status] [--memory]`

- No args → sync everything (Blog Posts both directions, Workspace Memory push) per the conflict rules below.
- `<SL#>` (e.g. `002`) → sync just that post (Blog Posts only).
- `--push` → force this repo's files to win for the given scope (still warns if Notion changed since last sync; asks before overwriting).
- `--pull` → force Notion to win for the given scope (same warning behavior). Not meaningful for `--memory` (one-way only) — ignored there.
- `--status` → dry run. Report what would change on each side, write nothing.
- `--setup` → first-run only: create the Notion database and the local state file (see Setup).
- `--memory` → sync only the Workspace Memory hub, skip Blog Posts.

## Setup (run once, or whenever `.notion-sync-state.json` is missing)

1. Confirm the Notion MCP tools are actually available this session (search `mcp__notion__*`). If not connected, tell the user to run `claude mcp auth notion` and stop — don't proceed on a guess.
2. If `.notion-sync-state.json` doesn't exist at the repo root, ask the user which Notion page/workspace location the database should live under, then create a database named "Blog Posts" with this schema:

   | Property | Type | Notes |
   |---|---|---|
   | Title | Title | EN Meta Title, or working title pre-draft |
   | SL# | Number | Stable key — matches the `posts/<SL#>-...` folder |
   | Status | Select | Idea / Research / Drafting / Fact-Check / Review / Publish-Ready / Published |
   | EN Status | Select | same options, plus N/A |
   | BN Status | Select | same options, plus N/A |
   | Slug | Text | EN frontmatter URL Slug |
   | Primary Keyword | Text | EN frontmatter |
   | Category | Select | EN frontmatter |
   | Draft Date | Date | most recent across languages |
   | Publish Date | Date | earliest live date, blank if unpublished |
   | Live URL | URL | `https://connect.panosia.com/posts/<slug>`, blank if unpublished |
   | Folder Path | Text | `posts/<SL#>-<slug>/` |
   | Social Posted | Multi-select | Facebook / Instagram / LinkedIn / X — one entry per platform with `Status: posted <date>` in *either* language's `<lang>/<SL#>-social-posts.md` |

3. Write `.notion-sync-state.json` at the repo root (add it to `.gitignore` if not already there — it's a local sync cache, not editorial content):

   ```json
   {
     "database_id": "<id>",
     "posts": {
       "002": {
         "notion_page_id": "<id>",
         "languages": {
           "en": {
             "article": { "file_mtime": null, "content_hash": null, "notion_last_edited": null },
             "social": { "file_mtime": null, "content_hash": null, "notion_last_edited": null }
           },
           "bn": {
             "article": { "file_mtime": null, "content_hash": null, "notion_last_edited": null },
             "social": { "file_mtime": null, "content_hash": null, "notion_last_edited": null }
           }
         }
       }
     }
   }
   ```

4. Run a full sync immediately after setup to populate every existing post.
5. Also run the Workspace Memory sync (below) so the hub exists from the start, and record its page IDs in the same state file under `"workspace_memory"`.

## Workspace Memory sync (repo → Notion, one-way)

Keeps the "Sam Workspace Memory" Notion hub current with the repo's own context files. This is push-only: the repo file is always authoritative, so there is no conflict logic here — just re-render each Notion page from its source file whenever the source changed since the last sync.

**Source → Notion page mapping** (one Notion page per row, all children of the hub page):

| Notion page | Source file(s) |
|---|---|
| 📊 Memory & Status | `MEMORY.md` |
| 📐 Editorial Workflow & Rules | `AGENTS.md` (workflow-relevant sections only — omit the RTK/CLI command reference, that's Claude-Code-tooling-specific, not editorial content) |
| 🎤 Brand Voice | `context/brand-voice.md` |
| 🏢 Site Profile | `context/site-profile.md` |
| 📝 User Notes | `context/user-notes.md` |
| ✍️ Writing & Review Standards | `docs/article-writing.md` + `docs/article-review.md` + `docs/image-workflow.md` + `templates/article-frontmatter.md` |
| 🔍 SEO Guidelines & Keywords | `context/seo-guidelines.md` + `context/target-keywords.md` + `context/internal-links.md` |

1. If `.notion-sync-state.json` has no `workspace_memory` block yet (first run), ask the user where the hub should live if not already clear from context (e.g. "same teamspace as the Blog Posts database?"), then create the hub page ("🧭 Sam Workspace Memory") and its 7 child pages per the table above. Record every page ID plus a content hash of each source file (or set of files) under `workspace_memory` in the state file:
   ```json
   "workspace_memory": {
     "hub_page_id": "<id>",
     "pages": {
       "memory_status": { "notion_page_id": "<id>", "sources": ["MEMORY.md"], "content_hash": "<sha256 of concatenated sources>" },
       "editorial_workflow": { "notion_page_id": "<id>", "sources": ["AGENTS.md"], "content_hash": "<hash>" },
       "brand_voice": { "notion_page_id": "<id>", "sources": ["context/brand-voice.md"], "content_hash": "<hash>" },
       "site_profile": { "notion_page_id": "<id>", "sources": ["context/site-profile.md"], "content_hash": "<hash>" },
       "user_notes": { "notion_page_id": "<id>", "sources": ["context/user-notes.md"], "content_hash": "<hash>" },
       "writing_review": { "notion_page_id": "<id>", "sources": ["docs/article-writing.md", "docs/article-review.md", "docs/image-workflow.md", "templates/article-frontmatter.md"], "content_hash": "<hash>" },
       "seo_guidelines": { "notion_page_id": "<id>", "sources": ["context/seo-guidelines.md", "context/target-keywords.md", "context/internal-links.md"], "content_hash": "<hash>" }
     }
   }
   ```
2. On later runs: for each row, hash the current source file(s) and compare to the stored `content_hash`. Unchanged → skip. Changed → replace that Notion page's content (`update-page` with `replace_content`, keeping the page's title/icon) with a re-rendered version of the source, ending with a small footer noting what it mirrors and the sync date, then update the stored hash.
3. Don't ask before pushing — this direction has no conflict risk (Notion side is never hand-edited as a source of truth), so just report what changed in the output summary.
4. If a mapped source file no longer exists, leave the Notion page in place but note it as stale in the output rather than deleting anything.

## Discovering posts, languages, and social copy

Scan `posts/*/` for bundles. For each `posts/<SL#>-<slug>/`, each `<lang>/<SL#>-article.md` present is one language to sync (Notion section `## <LANG> Draft`). If that language also has `<lang>/<SL#>-social-posts.md`, sync it too (Notion section `## <LANG> Social Posts`) — its `##` platform subsections (Facebook/LinkedIn/X/Instagram) carry straight over as sub-headings. A bundle with only `research.md` and no article yet still gets a row (Status: Research), with no language sections.

## Per-post, per-language sync

Run the same push/pull/conflict logic independently for each of a language's two possible content pieces — **article** and **social** — since either can change without the other:

1. Read the file's current mtime and a content hash.
2. Fetch the corresponding Notion section's content (`## <LANG> Draft` for article, `## <LANG> Social Posts` for social) and the page's `last_edited_time`.
3. Compare against `.notion-sync-state.json`'s last-synced values for that (post, language, piece):
   - **Neither side changed since last sync** → skip.
   - **Only the file changed** → push. For article: update Notion properties (from frontmatter) and replace `## <LANG> Draft` with the frontmatter (as a callout) + body. For social: replace `## <LANG> Social Posts` with the file's content as-is (its own per-platform Status lines carry over verbatim).
   - **Only Notion changed** → pull. For article: replace the file's body with Notion's section content, minus the frontmatter callout — never touch frontmatter fields that aren't also Notion properties (e.g. Hero Image), merge don't clobber. For social: replace the file's content with Notion's section content, preserving the `## Platform` structure.
   - **Both changed (real conflict)** → do not silently resolve, even in default last-write-wins mode. Show the user both versions' timestamps and a brief diff summary, name which side is more recent, and ask before overwriting. `--push`/`--pull` skip this prompt only for the scope explicitly forced.
4. After a successful push or pull, update the state file's hash/mtime/`notion_last_edited` for that (post, language, piece) so the next run has a clean baseline.
5. After syncing an article or social file (whichever direction), recompute that row's **Social Posted** multi-select from every `Status: posted <date>` line currently present across both languages' social files (post-sync state), and push it to Notion.

## New posts and posts missing from Notion

- A `posts/` bundle with no state-file entry → create its Notion row (and language sections) from the files; this is a push, no conflict possible.
- A Notion row with no matching `posts/` folder → flag it in the summary, don't delete anything. Deleting is the user's call.

## Status derivation (when pushing frontmatter → Notion)

Per language: no article file → N/A. Article exists, no `Publish Date` set → Drafting (or Fact-Check/Review if the user says a check already ran this session — otherwise default Drafting). `Publish Date` set → Published. Overall `Status` is the least-advanced of the language statuses that aren't N/A (e.g. EN Published + BN Drafting → overall Drafting), so the row never looks more done than its least-finished language.

## Guardrails

- Never invent a Notion page/database ID — always read it from `.notion-sync-state.json` or a tool result, never assume one from memory.
- Never delete a Notion page or a local file as part of a sync. Flag orphans, let the user decide.
- Always run `--status` first when asked to "check" or "preview" sync state — don't write on a read request.
- If Notion MCP tools are unavailable or auth has lapsed mid-run, stop and report exactly which posts were synced before the failure — don't leave the state file half-updated for a post that didn't actually complete.

## Output

After any sync (not `--status`), report per post: what pushed, what pulled, what was skipped as unchanged, and any conflicts that still need the user's call. Keep it a compact table, not a wall of prose. When a Workspace Memory sync ran too, add a short second table: which of the 7 pages pushed vs. skipped as unchanged.
