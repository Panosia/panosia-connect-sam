# Sam — Panosia Connect SEO Content Workspace

Sam is Panosia's maintained fork of an AI content writing agent, configured specifically for [Panosia Connect](https://connect.panosia.com) (connect.panosia.com). It researches topics, drafts SEO articles, fact-checks them, and reviews them for publish readiness — so content ships faster and consistent with the brand.

- **Model agnostic** — works with any model, in [OpenCode](https://opencode.ai/) or [Claude Code](https://claude.com/product/claude-code). A GPT 5.4 + OpenCode combination tends to produce the most natural drafts.
- **Built for real content work** — keyword direction, source checking, drafting, and review are handled end to end.
- **Easy to maintain** — the workspace is just files: brand context, drafts, and docs you can read and edit directly.

## Who this README is for

Panosia maintainers — the people who will keep this workspace running. That includes the founder, and anyone on the team who writes or reviews content for the site. If you're new here, start with [Quickstart](#quickstart).

## Quickstart

### Prerequisites

- A coding agent subscription (e.g., ChatGPT Plus/Pro) if you want GPT 5.4 in OpenCode.
- [OpenCode](https://opencode.ai/) or Claude Code installed locally.

### Setup

```bash
# Clone the Panosia fork
git clone https://github.com/Panosia/panosia-connect-sam

# Switch to the directory
cd panosia-connect-sam

# If you're using OpenCode with GPT 5.4, authenticate first
opencode auth login

# Open the agent and say "hi"
opencode
# or: claude
```

Say **"hi"** and Sam will orient itself from the workspace state and tell you the next useful step. Sam reads `MEMORY.md` first, so a new session always knows where things stand.

## How the workspace is organized

| Path | Purpose |
| --- | --- |
| `MEMORY.md` | Source of truth for setup status, known context, and next steps. Keep updated as strategy changes. |
| `context/` | Durable brand and strategy: site profile, brand voice, SEO guidelines, user notes, target keywords, internal links. |
| `docs/` | Guides Sam follows: setup, article writing, article review, DataForSEO MCP setup, Exa search setup. |
| `templates/` | Metadata blocks: article frontmatter, research brief. |
| `drafts/` | Article drafts, saved with lowercase date-stamped slugs (e.g., `drafts/how-to-find-a-life-partner-trust-first-guide-2026-08-05.md`). |
| `research/` | Research briefs and outputs. |
| `scripts/` | `analyze-draft.mjs` (SEO spot-check) and `normalize-draft.mjs` (formatting). |
| `AGENTS.md` | The rules Sam works under ("Sam Rules"). |

## Core workflow

1. **Onboarding** — say "hi"; Sam reads the site and fills in `context/` files, or resumes from `MEMORY.md` if setup already exists.
2. **Research & brief** — Sam proposes a primary keyword, search intent, angle, and outline before writing anything.
3. **Draft** — Sam writes the full article as a finished piece for readers.
4. **Fact-check** — a subagent verifies every link and claim; required fixes go straight into the draft.
5. **Independent review** — a fresh-context SEO review for intent, structure, evidence, and scannability.
6. **Publish** — drafts are bilingual-ready (English + Bengali), matching the site's EN/BN structure.

## Current setup state (as of 2026-08-05)

- **Status:** good enough — core context, brand voice, and starter keywords are in place. DataForSEO (external keyword/SERP data) was skipped for now and can be added later; the internal-links map is optional and deferred.
- **Company:** Panosia Connect — a trust-based matrimony platform with Candidate and Connector roles. Free to join, no subscriptions; optional one-time verification services are the only paid products.
- **Content strategy:** a role-based article series, one audience per piece:
  1. Candidate guide — drafted (how to find a life partner)
  2. Parents/family guide — next up
  3. Volunteer matchmaker guide
  4. Local professional matchmaker guide

## Extending the workspace

- Ask Sam to add MCP integrations (DataForSEO for high-confidence keyword data, Exa for web search) or publishing tools — it can update the workspace config to support them.
- Manual setup details live in `docs/setup-guide.md`; writing and review standards live in `docs/article-writing.md` and `docs/article-review.md`.

## License

See `LICENSE` for terms.
