# Image Workflow

Use this guide whenever a post bundle (`posts/<SL#>-<slug>/`) needs images.

## Where Images Live

- Images live in the post bundle's `images/` folder, shared across every language version of that post. A photo isn't language-specific, its alt text is.
- Created on first use. Don't pre-create an empty `images/` folder for a post that doesn't have images yet.

## Naming

- `hero.<ext>` — the post's hero/cover image: used at the top of the article and as the default share image.
- `image-1.<ext>`, `image-2.<ext>`, ... — in-body images, numbered in the order they appear in the article.
- Keep the original file extension (`.jpg`, `.png`, `.webp`).
- Prefer `webp` when there's a choice, it's the best balance of quality and file size for web use. `jpg`/`png` are fine when that's what the source provides.

## Alt Text

- **In-body images**: alt text lives inline in the Markdown embed, at the point of use, per language: `![alt text in that language](../images/image-1.webp)`. Each language's `article.md` writes its own alt text; unlike the image file, it isn't shared across languages.
- **Hero image**: rendered by the site template rather than embedded in the article body, so its reference and alt text live in the article's frontmatter instead:
  ```
  **Hero Image**: images/hero.webp
  **Hero Image Alt**: <alt text, in the article's own language>
  ```
  Both fields are optional until the post actually has a hero image, don't invent a placeholder image reference.

## Sourcing & Licensing

Every image needs a legitimate source: stock photography, an illustration, a brand graphic, or something the team has the rights to use. Track provenance so this stays checkable later:

- The first time an image is added to a post bundle, create `images/sources.md` alongside it.
- One line per image: filename, source (site/photographer/tool), license (e.g. "royalty-free," "licensed," "brand asset"), date added.
- Never use an image without knowing its license. If the source is uncertain, flag it rather than guessing or assuming it's fine.

## Format & Size Guardrails

- No image-optimization tooling exists in this repo yet, so check file size by hand: a hero image over roughly 500KB is worth compressing before committing.
- Prefer web-appropriate resolution (roughly 1200-2000px on the long edge for a hero image) over an uncompressed original straight out of a camera or design tool.
