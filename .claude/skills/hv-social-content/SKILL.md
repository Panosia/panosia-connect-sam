---
name: hv-social-content
description: Converts a published or publish-ready blog/article draft into platform-native social media post copy, acting as an industry-leading social content strategist and copywriter — finds the sharpest angle in the piece, writes hook-first copy tuned to how each platform's algorithm and reader actually behave, and stays inside house brand-voice guardrails the whole way. Use when the user invokes /hv-social-content or asks to turn a blog/article into a Facebook, Instagram, LinkedIn, or X post.
---

Think like a strategist first, a copywriter second. The job is not "summarize the article shorter." It's: find the one angle in this piece that would make someone stop scrolling, then write it the way that platform's best creators actually write, inside this brand's voice.

## Usage

`/hv-social-content <path> [--platform facebook|instagram|linkedin|x] [--variants N]`

- No path → ask, or offer the most recent publish-ready/published article's `<lang>/<SL#>-article.md` under `posts/` (or the language implied by context).
- No `--platform` → always ask which platform(s) (Facebook, Instagram, LinkedIn, X, or multiple), presenting Facebook as the pre-selected/default option, before writing any copy. Skip the ask only if the user's request already named a platform.
- No `--variants` → 1. `--variants 2` produces two hook variants (A/B) of the same post, clearly labeled, for the user to choose or test.

## Setup

Read in full: the source article; `context/brand-voice.md`; `context/site-profile.md`; `context/user-notes.md`. Check `MEMORY.md`'s Content Index for the article's publish status.

- **Published** → use its live URL (`https://connect.panosia.com/posts/<URL Slug>`).
- **Not yet published** (drafted, publish-ready, or under revision) → still write the post, but flag clearly that the link isn't live yet. Never assert a URL is live when it isn't.

If the draft is `bn`, write the post in Bengali and follow the bn terminology notes in `context/user-notes.md` (e.g. "বিশ্বাস যোগ্য" for trust-first framing).

## Strategist Pass (do this before writing any copy)

Read the article once for angles, not for summary. Look for the moment a reader would actually screenshot, share, or comment on:

- A sharp reframe or myth-bust ("verification doesn't prove character, it proves a person is real")
- A concrete list or checklist readers can act on immediately (red flags, a 4-list exercise, three things to check)
- A persona beat that makes an abstract point human (Sarah's four lists, Ryan checking connections before messaging)
- A founder/mission angle, if the article touches why the product exists
- A myth the target audience already believes, that the article quietly corrects

Pick the single strongest angle as the post's spine. Don't try to cover the whole article, that's what the link is for. A post that nails one angle outperforms one that summarizes five.

## Platform Playbook

Apply the mechanics for whichever platform(s) were requested. These are the load-bearing craft rules, not decoration:

| | Facebook | Instagram | LinkedIn | X |
|---|---|---|---|---|
| **Hook window** | ~3 lines / ~477 chars before "See more" | First 1–2 lines before "more" | First ~140 chars before "see more" | Full post is the hook, ~280 chars (or first tweet of a thread) |
| **Link placement** | Caption stays link-free; link goes in the **first comment** (protects reach vs. a link-preview post) | Link-free caption; "link in bio" or first comment | Native link post is fine, LinkedIn doesn't penalize it as hard as FB/IG | Link at the end, or in a reply if threading |
| **Hashtags** | 1–3 max, end of post | 5–15, end of caption or first comment | 3–5, end of post | 1–2, inline is fine |
| **Tone that works** | Warm, direct, personal | Visual-first, caption supports an image/carousel, not the other way around | Founder-voice, "why we built this," slightly more authoritative | Terse, one clear idea, no throat-clearing |
| **Format note** | Short paragraphs, emoji as visual bullets not decoration | Suggest an image/carousel concept alongside the caption, this platform is visual-first | Fine as straight prose, no emoji needed | Consider a 3–5 tweet thread if the angle needs more than one beat |

## Guardrails (non-negotiable)

- **No new claims.** Every fact, stat, or claim in the post must already exist in the source article. Converting to social is not a chance to add color that wasn't fact-checked upstream.
- **Brand voice applies in full**: no hype, no urgency/scarcity language, no guarantee-adjacent phrasing, no invented numbers, no engagement-bait questions. Re-check `context/brand-voice.md`'s "things to avoid" and "terms to avoid" lists before finalizing.
- **Product terms stay correct**: Candidate, Connector, Digital ID Verification, etc., capitalized and defined the way the article defines them, not re-simplified into something inaccurate.
- **One CTA.** Read the article, not read-and-signup-and-follow-and-share.
- **Never claim a link is live if the article isn't published yet.**

## Output

For each requested platform/variant, write a section with:

1. **Status**: `not yet posted` (default) — flip to `posted <date>` by hand once it's actually gone out.
2. One line of strategist rationale: which angle, and why it's the strongest hook in this piece.
3. The ready-to-post copy, exactly as it should be pasted.
4. Tactical notes: link placement (first comment vs. native), hashtags, an image/visual suggestion, and anything the human posting it needs to know (e.g. "confirm this URL is live before posting").

Save into the source article's own post bundle, at `posts/<SL#>-<topic-slug>/<lang>/<SL#>-social-posts.md`, one `##` section per platform (`## Facebook`, `## LinkedIn`, `## X`, `## Instagram`). If the file already exists, add or replace the sections for the requested platform(s) and leave the others untouched, don't overwrite the whole file. Don't create a separate strategy-notes file or a platform-specific file, the rationale and tactical notes live inline above and below the copy in the same section.
