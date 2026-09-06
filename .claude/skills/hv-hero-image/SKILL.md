---
name: hv-hero-image
description: Reads a blog post and writes 5 distinct Google Gemini image-generation prompt variations for an editorial, professional OG/hero image, appended to the bottom of the article's markdown file. Use when the user invokes /hv-hero-image or asks for hero image prompts, OG image prompts, or Gemini prompts for a blog post's cover image.
---

This skill writes prompts, it does not generate images. The output is 5 ready-to-paste text prompts for Google Gemini's image generator (or another Gemini-compatible tool). If the user wants the image actually rendered, that's `blog-image` (Gemini via MCP) — point them there instead of trying to generate pixels here.

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

Per `context/brand-voice.md`, this brand is warm, respectful, trustworthy, family-friendly, and explicitly **not** a dating-app aesthetic. Every prompt must:

- Read as editorial/documentary photography, not stock-photo cliché or illustration, unless the user asks for illustration instead
- Show warmth and dignity: real-feeling human moments (a conversation, a family gathering, a quiet decision), not posed "stock couple" tropes
- Avoid dating-app visual clichés: no swiping gestures, no phone screens showing a "match," no hearts/flames iconography
- Avoid literal security clichés for verification-themed posts: no padlocks, checkmarks, shield icons, or barcode-style ID graphics
- Respect the audience: modest, culturally appropriate representation fitting a Bangladeshi/South Asian and broader diaspora matrimony audience, never stereotyped or exoticized
- No embedded text, logos, or watermarks in the image itself — the site overlays the title separately. Flag this assumption to the user and skip it only if they explicitly want baked-in text.
- Landscape orientation suited to an OG/share image (1200×630, roughly 1.91:1) — say so explicitly in every prompt so Gemini frames it correctly.

## Writing the 5 Variations

Each variation must be a genuinely different angle on the article's subject, not five phrasings of the same shot. Vary at least two of: subject/protagonist, setting, composition (close-up vs. wide, candid vs. still-life/detail shot), time of day/lighting, or emotional register. Build each prompt from these components, in the prompt text itself (not as separate labeled fields):

1. **Subject** — who or what, grounded in the article's actual content (a specific persona moment if the article has one, e.g. Farida at a wedding; otherwise a representative, unnamed figure)
2. **Action** — what they're doing, a real moment not a pose
3. **Context/setting** — where, matching the article's world (a family gathering, a quiet home office, a community space)
4. **Composition** — framing, angle, depth of field
5. **Lighting** — natural light descriptors (soft morning light, warm golden hour, diffused window light) — avoid harsh studio lighting
6. **Style** — "editorial photography," "documentary style," a film stock or photographer-reference adjective if it helps (warm, muted, natural tones), plus the aspect ratio line

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
...through Variation 5
```

Use `Edit`/insert at the end of the file, don't rewrite the rest of the article. If the section already exists (a re-run), replace it rather than duplicating it.

## Placement Across Languages

Per `docs/image-workflow.md`, a hero image is one shared asset per post bundle, not per language. If the post has multiple language versions, add this section only to the article file the user pointed at (or the `en` one by default if generating fresh) — don't duplicate it into every language's file. If the section already exists in a sibling-language file, tell the user instead of writing a second copy.

## After Writing Prompts

Remind the user this only produced prompts: they (or `blog-image`) still need to run one through Gemini, pick a result, save it as `images/hero.webp` per `docs/image-workflow.md`, and set the `Hero Image` / `Hero Image Alt` frontmatter fields. Don't set those frontmatter fields yourself until an actual image exists, an unset reference gets treated as a real hero image by the site template.
