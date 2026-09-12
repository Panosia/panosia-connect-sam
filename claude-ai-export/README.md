# Claude.ai / Claude Desktop Export

Six standalone Agent Skills adapted from this repo's `.claude/skills/` and `.claude/agents/` for use outside Claude Code, where there's no filesystem to read `context/`, `docs/`, `MEMORY.md`, etc. Each `SKILL.md` inlines the relevant house rules and Panosia Connect brand-voice defaults directly, and works from pasted context (draft text, brand notes, keyword data) instead of file paths.

| Skill | Replaces |
|---|---|
| `sam-article-writer` | `.claude/agents/article-writer.md` + `docs/article-writing.md` |
| `sam-fact-checker` | `.claude/agents/fact-checker.md` |
| `sam-bn-translator` | `.claude/agents/bn-translator.md` |
| `sam-article-review` | `.claude/skills/hv-article-review/` + `.claude/agents/seo-reviewer.md` + `docs/article-review.md` |
| `sam-social-content` | `.claude/skills/hv-social-content/` |
| `sam-hero-image-prompts` | `.claude/skills/hv-hero-image/` |

Not exported: `.claude/agents/seo-guide.md` (an orchestrator that assumes this repo's file layout — Claude.ai's own chat/Project already plays that role) and `.claude/skills/hv-notion-sync/` (pure repo-to-Notion sync infrastructure, nothing to port).

## Install

1. Zip each skill's own folder (the folder must contain `SKILL.md` at its root), e.g.:
   ```
   cd claude-ai-export/sam-article-writer && zip -r ../sam-article-writer.zip . && cd -
   ```
   (already done for all six — see the `.zip` files alongside each folder)
2. In Claude.ai or Claude Desktop: **Settings → Capabilities → Skills → Upload skill**, and upload the zip.
3. Repeat per skill.

## Caveats

- These carry the Panosia Connect brand-voice defaults (tone, vocabulary, claims to avoid) baked in as a fallback. For other projects, paste your own brand notes when using the skill and it'll use those instead.
- No filesystem access on Claude.ai web: paste drafts/context directly into the chat. On Claude Desktop with a filesystem/MCP connection to this repo, you can instead point the skill at real file paths and it'll behave close to the original Claude Code versions.
- The `sam-article-writer` and `sam-bn-translator` skills reference sitemap/live-link verification steps from the original — without web access in a given session, they'll flag links as unverified rather than confirming them, which is the safe fallback.

## Notion as the context source (recommended for Claude.ai / Desktop without repo access)

This repo already syncs to Notion via `hv-notion-sync`: a "Blog Posts" database (per-post status, EN/BN draft content, social copy) plus a "🧭 Sam Workspace Memory" hub (Brand Voice, User Notes, Site Profile, Writing & Review Standards, SEO Guidelines & Keywords — mirrored one-way from this repo's own context files).

All six skills here now check for Notion MCP first before asking you to paste anything:

1. If Notion MCP tools are available in that Claude.ai/Desktop session, and the user has connected the same Notion workspace and shared the Blog Posts DB / Workspace Memory hub with the integration, the skill queries them directly — current brand voice, house rules, and a named post's draft content, without you copy-pasting.
2. If Notion isn't connected, or a page isn't shared with the integration, it falls back to asking you to paste that context.
3. Only as a last resort does it fall back to the defaults baked into the `SKILL.md` file itself (which can go stale if the repo's context files change and Notion hasn't been re-synced, or Notion isn't reachable).

Setup, one-time: in Claude.ai/Desktop, connect the Notion integration under Settings → Connectors, and make sure it has access to the same Notion workspace/pages this repo's `hv-notion-sync` created. Permission is workspace/page-level (granted once when you share a page with the integration), not a separate prompt per fact it reads. This repo stays the source of truth; run `/hv-notion-sync` here after editorial changes so Notion (and therefore these exported skills) don't drift stale.
