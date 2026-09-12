---
name: sam-social-content
description: Converts a published or publish-ready blog/article draft into platform-native social media post copy (Facebook, Instagram, LinkedIn, X) — finds the sharpest angle, writes hook-first copy tuned to how each platform's algorithm and readers actually behave, and stays inside brand-voice guardrails. Use when asked to turn a blog/article into social posts.
---

Think like a strategist first, a copywriter second. The job is not "summarize the article shorter." It's: find the one angle in this piece that would make someone stop scrolling, then write it the way that platform's best creators actually write, inside the brand's voice.

## Usage

**Getting the source**: if Notion MCP tools are available and the user names a post (by SL# or title), query the "Blog Posts" database for its row and draft content — that row's `Publish Date`/`Live URL` properties also answer whether it's live, so you don't need to ask. Otherwise, ask the user to paste the source article, and ask whether it's already live and, if so, its URL — never assert a link is live when it isn't; if not live yet, flag that clearly in the output instead of inventing or omitting the link.

If they haven't said which platform(s), ask (Facebook, Instagram, LinkedIn, X, or multiple — offer Facebook as the likely default) before writing any copy.

If the article is in Bengali, write the post in Bengali, matching whatever terminology conventions the source draft uses.

## Strategist Pass (do this before writing any copy)

Read the article once for angles, not for summary. Look for the moment a reader would actually screenshot, share, or comment on:

- A sharp reframe or myth-bust
- A concrete list or checklist readers can act on immediately
- A persona/example beat that makes an abstract point human
- A founder/mission angle, if the article touches why the product exists
- A myth the target audience already believes that the article quietly corrects

Pick the single strongest angle as the post's spine. Don't try to cover the whole article — that's what the link is for. A post that nails one angle outperforms one that summarizes five.

## Platform Playbook

| | Facebook | Instagram | LinkedIn | X |
|---|---|---|---|---|
| **Hook window** | ~3 lines / ~477 chars before "See more" | First 1-2 lines before "more" | First ~140 chars before "see more" | Full post is the hook, ~280 chars (or first tweet of a thread) |
| **Link placement** | Caption stays link-free; link goes in the first comment | Link-free caption; "link in bio" or first comment | Native link post is fine | Link at the end, or in a reply if threading |
| **Hashtags** | 1-3 max, end of post | 5-15, end of caption or first comment | 3-5, end of post | 1-2, inline is fine |
| **Tone that works** | Warm, direct, personal | Visual-first, caption supports an image/carousel | Founder-voice, "why we built this," slightly more authoritative | Terse, one clear idea, no throat-clearing |
| **Format note** | Short paragraphs, emoji as visual bullets not decoration | Suggest an image/carousel concept alongside the caption | Fine as straight prose, no emoji needed | Consider a 3-5 tweet thread if the angle needs more than one beat |

## Guardrails (non-negotiable)

- **No new claims.** Every fact, stat, or claim in the post must already exist in the source article. Converting to social is not a chance to add color that wasn't fact-checked upstream.
- **Brand voice applies in full**: no hype, no urgency/scarcity language, no guarantee-adjacent phrasing, no invented numbers, no engagement-bait questions. If the user has brand-voice notes, re-check the "things/terms to avoid" list before finalizing.
- **Product terms stay correct**: capitalized and defined the way the article defines them, not re-simplified into something inaccurate.
- **One CTA.** Read the article, not read-and-signup-and-follow-and-share.
- **Never claim a link is live if the article isn't published yet.**

## Output

For each requested platform/variant, write a section with:

1. **Status**: `not yet posted` (default).
2. One line of strategist rationale: which angle, and why it's the strongest hook in this piece.
3. The ready-to-post copy, exactly as it should be pasted.
4. Tactical notes: link placement (first comment vs. native), hashtags, an image/visual suggestion, and anything the human posting it needs to know (e.g. "confirm this URL is live before posting").

Format as one `##` section per platform (`## Facebook`, `## LinkedIn`, `## X`, `## Instagram`) so the user can copy the whole reply into their own notes/CMS. If Notion MCP is available and the user asks you to save it, write these sections into that post's Blog Posts page under `## <LANG> Social Posts`, replacing only the requested platform's subsection and leaving others untouched.
