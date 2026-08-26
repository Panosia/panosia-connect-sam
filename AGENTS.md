# Sam Rules

This project is a standalone, OpenCode-native SEO content workspace.

## Workflow

1. Research a topic
2. Build a brief
3. Draft or revise the article
4. Fact-check substantial drafts and incorporate required fixes
5. Independently review for final publish readiness and incorporate required fixes

Substantial draft work means a new full draft, a full-article rewrite, or structural changes across multiple sections. It does not mean small local edits.

## Core Rules

- Do not assume Claude-specific features or hidden auto-execution chains.
- Do not invent analytics or keyword data unless the user provides it.
- Prefer explicit files on disk over conversational-only output.
- Keep the workflow generic enough for blogs, SaaS sites, agencies, and content teams.
- Use `MEMORY.md` as the source of truth for setup status and next steps.
- Treat `context/user-notes.md` as user-owned durable memory.
- If context is still blank or placeholder-heavy, begin setup in chat.
- If a live site exists, read beyond the homepage before drafting setup assumptions.
- For net-new drafts and major rewrites, fetch `https://connect.panosia.com/sitemap-posts.xml` (and `sitemap-static.xml` if relevant) once before drafting and reuse it for internal links, the Related Posts section, and the publish-slug check. Treat the live sitemap as the source of truth over `context/internal-links.md` or `MEMORY.md`, which can drift from what's actually published — fix those files on any mismatch.
- Keep `MEMORY.md` updated when setup progress or core strategy assumptions change.
- Every post lives in one page-bundle folder: `posts/<SL#>-<topic-slug>/`, e.g. `posts/001-how-to-find-a-life-partner-trust-first-guide/`. The SL# and slug live once, on the folder, not repeated on every file inside it. Give every post a zero-padded serial number (SL#), so posts stay easily identifiable and sortable by creation order regardless of title changes. Track the next available SL# and the SL# → title/slug mapping in `MEMORY.md`. The folder name carries no date; dates live in each language's own frontmatter instead (`Draft Date`, `Publish Date` — see `templates/article-frontmatter.md`), since a translation is drafted and published on its own timeline, not the English source's.
- Inside a post bundle:
  - `research.md` — the brief, if one was written (optional, shared across languages).
  - `<lang>/<SL#>-article.md` — the draft, one subfolder per language, including the default English one (`en/`, `bn/`, etc.), never a flat file directly in the bundle. The draft file itself is named just `<SL#>-article.md` (no topic slug in the filename, only on the parent folder), so it stays identifiable if the article is opened outside its folder context. Every language stays on equal footing; a translation reuses its English sibling's bundle, just under its own language folder.
  - `<lang>/<SL#>-social-posts.md` — social copy for that language, created once any exists, one `##` section per platform (see `hv-social-content`).
  - `images/` — shared across languages, created on first use. See `docs/image-workflow.md` for naming, alt text, and licensing.

## Load On Demand

- `MEMORY.md`
- `docs/setup-guide.md`
- `docs/article-writing.md`
- `docs/article-review.md`
- `docs/dataforseo-mcp-setup.md`
- `docs/exa-seup.md`
- `docs/image-workflow.md`
- `context/user-notes.md`
- `context/site-profile.md`
- `context/brand-voice.md`
- `context/seo-guidelines.md`
- `context/internal-links.md`
- `context/target-keywords.md`
- `templates/research-brief.md`
- `templates/article-frontmatter.md`

## Writing

- For net-new articles, prefer a compact pre-draft mini-brief that states the proposed keyword, likely search intent, suggested angle, working outline, and any source gaps before writing.
- Ask one bundled user check-in for outline preferences, must-use sources, must-cover points, claims to avoid, or other constraints unless they clearly want an immediate draft.
- Start with the reader's real problem or decision and get to the useful answer quickly.
- Keep the opening concrete rather than explaining the article or writing approach.
- Keep paragraphs short, specific, and easy to scan.
- Use concrete examples and natural internal links.
- Keep metadata concise and publication-ready.
- Treat methodology notes, inclusion filters, and exclusion lists as internal unless they materially help the reader.
- Drafts should read like finished articles for readers, not like transparent SEO or research process notes.
- Keep the writing practical, specific, and natural.

## Checks

- When a draft exists, prefer `node ./scripts/analyze-draft.mjs <path> --keyword "..."` before final optimization advice.
- Use `node ./scripts/normalize-draft.mjs <path>` only when the user asks for normalization or the file clearly needs it.
- Keep fact-check and review findings in-session. Incorporate required fixes into the draft instead of saving separate review markdown files.
- Treat a publish-ready draft with only optional polish remaining as the default end state for substantial draft work.
- If external keyword or SERP data is available, use it when it materially improves research confidence. DataForSEO via MCP is one good recommendation when the user wants the highest-confidence data, but it is optional.
- If the user wants DataForSEO but its MCP tools are not available in the current session, do not act like it is configured. Ask whether they want to set it up now or be reminded later, and if the runtime is unclear ask whether they are using OpenCode or Claude Code before giving setup commands. Record that answer in `MEMORY.md`, and read `docs/dataforseo-mcp-setup.md` before explaining the setup steps.

## Agents

- `seo-guide` is the user-facing orchestrator.
- Use `article-writer` for net-new drafts, major rewrites, and substantive prose revisions after review.
- Use `fact-checker` after new full drafts and major rewrites, and return findings in-session.
- Use `seo-reviewer` as the final independent fresh-context review after factual fixes are incorporated.
- Use `bn-translator` for translating English drafts into Bengali (bn), or polishing an existing rough/machine-translated bn draft against its English source.
- Skip the review loop for tiny edits.
