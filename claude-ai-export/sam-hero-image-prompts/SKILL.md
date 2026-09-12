---
name: sam-hero-image-prompts
description: Reads a blog post and writes 7 distinct Google Gemini image-generation prompt variations for a professional OG/hero image (5 editorial-photography angles, 1 abstract/graphic concept, and 1 title-baked variant of that abstract concept). Use when asked for hero image prompts, OG image prompts, or Gemini prompts for a blog post's cover image.
---

This skill writes prompts, it does not generate images. The output is 7 ready-to-paste text prompts for Google Gemini's image generator (or another Gemini-compatible tool).

## Usage

**Getting the article**: if Notion MCP tools are available and the user names a post (by SL# or title), query the "Blog Posts" database and fetch its draft content directly. Otherwise, ask the user to paste the full article (frontmatter + body) — never guess the article's content from its title alone.

## Understand the Article First

Pull out: the real subject (not the SEO keyword, the actual human moment or idea the piece centers on); the intended reader; and, if the user has brand-voice notes, load those guardrails too.

## Visual Direction (default guardrails — adjust if the user gives different brand guidance)

- Editorial/documentary or magazine-editorial photography, not stock-photo cliché or illustration (unless the user asks for illustration).
- Warm, dignified, real-feeling human moments, not posed "stock" tropes.
- No category-specific visual clichés the brand would want to avoid (ask the user if unsure — e.g. a dating brand avoiding swipe/heart iconography, a security brand avoiding padlock/checkmark cliché).
- International audience by default: vary ethnic/cultural background across variations rather than defaulting the whole set to one region; whatever background is depicted, keep it modest and dignified, never stereotyped.
- No embedded text/logos/watermarks unless the user asks.
- Landscape 1200×630 (~1.91:1) — state this explicitly in every prompt.
- Vary lighting, color, and style deliberately per variation rather than repeating one recipe: mix morning/overcast/golden-hour/blue-hour/lamplight/high-key, muted/warm/cool/bolder palettes, and documentary vs. glossy magazine-editorial styling.

## Writing Variations 1-5 (Editorial Photography)

Each must be a genuinely different angle, not five phrasings of one shot — vary at least three of: subject, setting, composition, lighting/color, style. Cover in the prompt's own text (not as labeled fields): **subject** (grounded in the article's real content), **action** (a real moment, not a pose), **setting**, **composition** (framing/angle/depth of field), **lighting and color**, **style** (plus a film-stock or photographer-reference adjective if it helps).

## Writing Variation 6 (Abstract/Graphic)

A non-literal option: the article's central idea rendered as shape, texture, and color rather than people or scenes. Avoid the generic "blue gradient with dots and lines" AI-abstract cliché specifically; any palette is fine as long as it reads as considered and human, not a stock tech-dashboard graphic. Same no-text/no-logo/aspect-ratio rules as variations 1-5. Name the concrete visual metaphor in the one-line rationale.

## Writing Variation 7 (Abstract + Title)

The same abstract concept as Variation 6, but with the article's exact Meta Title rendered into the image (a graphic/abstract background is more forgiving of imperfect text rendering than a photographic scene). Add: the exact title text (quoted verbatim), a request for clean modern sans-serif typography, high contrast for legibility at thumbnail size, and title placement that doesn't collide with the composition's focal point. Note in the rationale that Gemini's text rendering is unreliable and the result may need manual retouching or a design tool as a fallback.

## Output Format

```
## Hero Image Prompts (Google Gemini)

### Variation 1 — <short concept label>
<one-line rationale: why this angle fits the article>

```
<the full ready-to-paste prompt text>
```

### Variation 2 — ...
...through Variation 5 (editorial photography)

### Variation 6 — Abstract: <concept label>
...

### Variation 7 — Abstract + Title: <concept label>
...
```

## After Writing Prompts

Remind the user this only produced prompts: they still need to run one through Gemini (or an equivalent tool), pick a result, and save/set it as the article's hero image. Don't claim an image exists — this skill never generates pixels.
