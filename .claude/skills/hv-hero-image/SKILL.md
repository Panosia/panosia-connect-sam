---
name: hv-hero-image
description: Reads a blog post and writes 7 distinct Google Gemini image-generation prompt variations for a professional OG/hero image (5 editorial-photography angles, 1 abstract/graphic concept, and 1 title-baked variant of that abstract concept), appended to the bottom of the article's markdown file. Use when the user invokes /hv-hero-image or asks for hero image prompts, OG image prompts, or Gemini prompts for a blog post's cover image.
---

This skill writes prompts, it does not generate images. The output is 7 ready-to-paste text prompts for Google Gemini's image generator (or another Gemini-compatible tool). If the user wants the image actually rendered, that's `blog-image` (Gemini via MCP) — point them there instead of trying to generate pixels here.

## Usage

`/hv-hero-image [<path>]`

- `<path>` → a `<lang>/<SL#>-article.md` file. Read it in full.
- No path → ask which article. If context makes it obvious (the article just drafted or reviewed this session), offer that as the default rather than making the user repeat the path.
- Never guess the article's content from its title alone — always read the full file before writing prompts.

## Understand the Article First

Read the whole article (frontmatter + body), plus `context/brand-voice.md` and `context/site-profile.md` if not already loaded this session. Pull out:

- The real subject: not the SEO keyword, the actual human moment or idea the piece centers on (a parent's scattered network, a Candidate reading a profile like a family would, the resume-for-your-life-partner reframe, etc.)
- The intended reader (Candidate, parent, prospective volunteer/professional matchmaker) from `AGENTS.md`'s role-based series
- Language: if the source is a `bn` article, the visual concept still comes from the same universal human moment, no need for a separate bn-specific image (see Placement below)

## Visual Direction (non-negotiable guardrails)

Per `context/brand-voice.md`, this brand is warm, respectful, trustworthy, family-friendly, and explicitly **not** a dating-app aesthetic. Apply to every variation:

- Editorial/documentary or magazine-editorial photography, not stock-photo cliché or illustration (unless the user asks for illustration)
- Warm, dignified, real-feeling human moments, not posed "stock couple" tropes
- No dating-app clichés (swiping, "match" screens, hearts/flames) or verification-post clichés (padlocks, checkmarks, shields, barcodes)
- International audience, not Bangladesh/South-Asian-only, even though bn is one supported language: vary ethnic/cultural background across variations rather than defaulting the whole set to one region; whatever background is depicted, keep it modest and dignified, never stereotyped
- No embedded text/logos/watermarks (the site overlays the title) unless the user asks
- Landscape 1200×630 (~1.91:1) — state this explicitly in every prompt
- Vary lighting, color, and style deliberately per variation rather than repeating one recipe: mix morning/overcast/golden-hour/blue-hour/lamplight/high-key, muted/warm/cool/bolder palettes, and documentary vs. glossy magazine-editorial styling — don't default the whole set to golden-hour warm-muted

## Writing Variations 1–5 (Editorial Photography)

Each must be a genuinely different angle, not five phrasings of one shot — vary at least three of: subject, setting, composition, lighting/color, style. Cover these components in the prompt's own text (not as labeled fields): **subject** (grounded in the article's real content — a specific persona moment if one exists, e.g. Farida at a wedding, otherwise a representative figure), **action** (a real moment, not a pose), **setting** (matching the article's world), **composition** (framing/angle/depth of field), **lighting and color** (see guardrails), **style** (see guardrails, plus a film-stock or photographer-reference adjective if it helps).

## Writing Variation 6 (Abstract/Graphic)

A non-literal option: the article's central idea rendered as shape, texture, and color rather than people or scenes — e.g. threads converging into a network for a "trusted network" post, overlapping translucent layers for a "privacy control" post. Avoid the generic "blue gradient with dots and lines" AI-abstract cliché specifically; otherwise any palette is fine as long as it reads as considered and human, not a stock tech-dashboard graphic. Same no-text/no-logo/aspect-ratio rules as variations 1–5. Name the concrete visual metaphor in the one-line rationale so the user can judge if it maps to the article.

## Writing Variation 7 (Abstract + Title)

The same abstract concept as Variation 6, but with the article's exact `Meta Title` (from frontmatter) rendered into the image, since a graphic/abstract background is far more forgiving of Gemini's imperfect text rendering than a photographic scene. Add to the prompt: the exact title text (quoted verbatim), a request for clean modern sans-serif typography, high contrast against the background so it stays legible at OG-thumbnail size, and title placement (e.g. lower third or centered) that doesn't collide with the composition's focal point. Note in the rationale that Gemini's text rendering is unreliable and the result may need manual retouching or a design tool as a fallback.

## Output Format

Append to the bottom of the article file passed in (or chosen), under a new `##` section:

```
## Hero Image Prompts (Google Gemini)

### Variation 1 — <short concept label>
<one-line rationale: why this angle fits the article>

\```
<the full ready-to-paste prompt text>
\```

### Variation 2 — ...
...through Variation 5 (editorial photography)

### Variation 6 — Abstract: <concept label>
...

### Variation 7 — Abstract + Title: <concept label>
...
```

Use `Edit`/insert at the end of the file, don't rewrite the rest of the article. If the section already exists (a re-run), replace it rather than duplicating it.

## Placement Across Languages

Per `docs/image-workflow.md`, a hero image is one shared asset per post bundle, not per language. If the post has multiple language versions, add this section only to the article file the user pointed at (or the `en` one by default if generating fresh) — don't duplicate it into every language's file. If the section already exists in a sibling-language file, tell the user instead of writing a second copy.

## After Writing Prompts

Remind the user this only produced prompts: they (or `blog-image`) still need to run one through Gemini, pick a result, save it as `images/hero.webp` per `docs/image-workflow.md`, and set the `Hero Image` / `Hero Image Alt` frontmatter fields. Don't set those frontmatter fields yourself until an actual image exists, an unset reference gets treated as a real hero image by the site template.
