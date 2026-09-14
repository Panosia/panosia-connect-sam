# Image Workflow

Use this guide whenever a post bundle (`posts/<SL#>-<topic-slug>/`) needs images.

## Two Sources: New Images vs. Reusing a Live Screenshot

- **A new image** (a photo, illustration, or a screenshot that doesn't exist anywhere on the live site yet): follow the local-storage workflow below (`images/` folder, numbered filenames, `sources.md` entry).
- **Reusing an existing, already-published product screenshot** (e.g. an in-body image from another `posts/*` article, illustrating a real feature the current article also describes): hotlink it directly from the live site's own asset URL (e.g. `https://connect.panosia.com/assets/<hashed-name>.webp`) rather than downloading a copy. This is the preferred path for this case (confirmed 2026-09-13; article #4 established the pattern with 9 hotlinked screenshots before this was formalized). Reasoning: it's the same asset either way, a local copy would just be a second file to keep in sync if the source changes, and the site already serves it reliably.
  - Use the real `alt` text already established for that image where one exists (check other `posts/*/en/*-article.md` files that use the same asset), so the same screenshot doesn't earn conflicting descriptions across articles.
  - Note the reuse inline is not required, but do log it in the citing article's own bundle: add a line to that bundle's `images/sources.md` (create the file/folder if this is the bundle's first image) recording the hotlinked URL and which other post it was first published on, so the dependency on that URL staying live is traceable later.
  - Re-verify the hotlinked URL still resolves before publish, same as any other internal link — a landing/site restructure can change or remove these hashed asset paths.

## Where New Images Live

- Images live in the post bundle's `images/` folder, shared across every language version of that post. A photo isn't language-specific, its alt text is.
- Created on first use. Don't pre-create an empty `images/` folder for a post that doesn't have images yet.

## Naming

- `hero.<ext>` — the post's hero/cover image: used at the top of the article and as the default share image.
- `image-1.<ext>`, `image-2.<ext>`, ... — in-body images, numbered in the order they appear in the article.
- Keep the original file extension (`.jpg`, `.png`, `.webp`).
- Prefer `webp` when there's a choice, it's the best balance of quality and file size for web use. `jpg`/`png` are fine when that's what the source provides.

## Alt Text

- **In-body images**: alt text lives inline in the Markdown embed, at the point of use, per language: `![alt text in that language](../images/image-1.webp)`. Each language's `<SL#>-article.md` writes its own alt text; unlike the image file, it isn't shared across languages.
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
