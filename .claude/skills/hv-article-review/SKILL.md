---
name: hv-article-review
description: Multi-persona readability and publish-readiness review of a draft article — reads it through six required reader lenses (native English, diaspora/immigrant English, young, divorced mid-age, unfamiliar-with-Panosia-Connect, industry editor) plus relevant supporting lenses and structural checks, then triages everything with editorial judgment into one consolidated, actionable review. Use when the user invokes /hv-article-review or asks for a persona-based or multi-reader review of a draft.
---

Gather findings through personas; report as an editor, not a panel. Output is one consolidated, actionable review — never six separate reviews, a raw findings dump, or a saved audit file.

## Usage

`/hv-article-review <path> [--keyword "primary keyword"]`

No path given → ask, or use the most recently edited file in `drafts/` if context makes it obvious. No `--keyword` → read `Primary Keyword` from the draft's frontmatter.

## Setup

Read: the draft in full; `context/brand-voice.md`, `context/user-notes.md`, `context/seo-guidelines.md`, `context/site-profile.md` (for product-accuracy and the unfamiliar-reader lens); `docs/article-writing.md` and `docs/article-review.md` (house rules). Load `context/target-keywords.md` / `context/internal-links.md` only if they materially affect the review.

Run `node ./scripts/analyze-draft.mjs <path> --keyword "..."` when a keyword is available — deterministic support, not the source of truth.

Assume deep fact-checking already ran (`article-writer` → `fact-checker` → `seo-reviewer` workflow) unless told otherwise; still flag anything unsupported, invented, or risky.

## Personas

Read the draft once fully, then once per lens below. Per persona, note only what's distinctive to that lens — friction, confusion, drop-off, trust reaction. Never log the same observation under two personas; it belongs to whichever lens hits it hardest.

**Required (all six, every run):**

| Persona | Judges |
|---|---|
| Native English reader | Voice, rhythm, filler, stiff or translated-sounding phrasing. Highest bar for prose quality. |
| Diaspora / immigrant English reader | Plain language, idioms, sentence length, cultural assumptions. The project's actual core audience — weight this one heavily. |
| Young reader | Relevance to someone earlier in life or newer to the topic; flags content written only for an older audience. |
| Divorced, mid-age reader | First-marriage-only assumptions; tone that reads as judgmental or naive to someone with more life experience. |
| Unfamiliar with Panosia Connect | Self-containment — Candidate, Connector, verification, and any product term defined in plain language on first use. |
| Industry-leading editor (Forbes / NYT caliber) | Structure, headline/subhead craft, opening strength, cliché density, earned vs. asserted claims. The harshest lens. |

**Supporting (apply only when the draft's topic makes them relevant; skip silently otherwise):**

- **Scam-wary reader** — trust/safety claims earned and specific, not reassuring-sounding filler.
- **Interfaith / cross-cultural reader** — religious/cultural references read as illustrative, not the only valid path.
- **Low-tech-literacy / mobile skimmer** — scannability on a small screen; headings alone tell a coherent story.
- **Legal/compliance-conscious reader** — cross-check `brand-voice.md`'s claims-to-avoid list (success rates, "safest" absolutes, guarantees) for overclaiming that isn't factually wrong but is still risky.
- **Competitor / industry insider** — differentiation claims fair, specific, non-defensive.

Add another lens only if it would surface something none of the above catches (e.g. bn-translation-readiness for a piece likely to be translated soon), and say why. Don't pad the review with lenses that produce nothing.

## Structural Checks

Opening strength (reader/problem/promise within ~120-150 words); heading hierarchy; keyword placement without stuffing; title/meta quality; duplication within the piece and against other `drafts/en/` posts in the same series; em dash overuse; brand voice/vocabulary alignment; research-note or methodology leakage; FAQ presence; internal links relevant and sitemap-verified before publish.

## Triage

Before writing anything for the user, sort every finding into exactly one bucket:

1. **Fix.** Anything a reader would actually trip on, or required by house rules or claims risk. Includes cheap, clearly-correct "optional polish" — fold it in as a fix, don't present it as a lesser tier.
2. **Deliberately skipped.** Valid but not worth taking: duplicates ground another article owns, trades a concrete detail for a box-checking gesture, or adds scope the piece doesn't need. Keep one line explaining why, so the user can overrule it.
3. **Drop.** Nitpicks and stylistic disagreements with no real reader cost. Don't mention these at all — a review padded with harmless non-issues buries the ones that matter.

Resolve persona conflicts yourself (e.g. editor lens wants tighter prose, diaspora lens wants more scaffolding) and state which way you went and why. Convergent findings (3+ lenses, same issue) are the top-priority fixes.

## Output

1. Verdict + one-line summary of what the draft needs, first.
2. Fixes as a short prioritized checklist — reader problem, not copy-pasteable reviewer phrasing. Cite the persona only when that context helps a fix make sense.
3. Skipped items, one line each.
4. Nothing else. In-session only, no saved review file.

Verdict labels:

- `publish-ready` — no fixes.
- `publish after required fixes` — fixes exist but are light/mechanical (wording, metadata, a defined term, a trimmed redundancy).
- `needs substantial revision` — fixes require structural change, a thesis gap, or unresolved factual/claims risk.

## Applying Fixes

Light, surgical pass by default. Route fixes straight into the draft (`article-writer` for substantive prose, direct edit for mechanical ones) — never into a separate review artifact. Save durable, recurring feedback (tone, persona blind spots) to `context/user-notes.md`.
