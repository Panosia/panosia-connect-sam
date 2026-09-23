# Research Brief: SL#015 — Serious Matrimony Later in Life

## Source

Notion Blog Posts DB, Priority 12, OpenSEO-validated (real DataForSEO search-volume data, not a guess).

## Working Title

"Serious Matrimony Later in Life: What Older Candidates Should Look For"

## Persona

Serious Candidate — specifically an older adult (widowed, divorced, or never married) seeking a serious life partner.

## Keywords

- Primary: "senior dating sites" (14,800/mo, commercial intent)
- Secondary: "dating for seniors" (2,400/mo, informational)
- Secondary: "free senior dating sites" (3,600/mo, commercial)

## Competitive Landscape

SilverSingles and SeniorMatch dominate this keyword space, but both run a mainstream swipe/casual-dating-app model. Per `context/brand-voice.md`, competitors are not named directly in the draft ("without attacking competitors by name") — the category/model is described generically instead ("most senior dating sites are built around casual dating mechanics, not marriage").

## Core Thesis

An older Candidate searching for a serious life partner has different needs than the swipe-based "senior dating" category assumes. Family involvement, identity verification, and a non-casual framing matter even more at this life stage, not less. The article positions itself as "matrimony for older adults," explicitly distinct from "senior dating" as a category.

## Reader

An older adult (widowed, divorced, or never married) seeking a serious life partner, who currently only finds generic "senior dating" sites built around casual dating mechanics, and does not see anything built for what they actually want (marriage, not dates).

## Angle

Why "senior dating" sites are not built for someone seeking marriage specifically, and what a trust-first, family-involved approach looks like at this life stage instead.

## Explicitly Avoided

- Ageist or pitying framing. The reader is a full adult making a serious, deliberate decision, the same as any other Candidate persona in this workspace.
- Conflating this with the separate, more sensitive Divorced/Widowed-stigma angle. That stays a different topic for a different day; this piece stays narrowly on the practical "what should I actually look for/check" question.
- Naming SilverSingles or SeniorMatch by name.

## Product Mechanics Used (from `context/site-profile.md`)

- **Managed Profiles** (PRD-01/19) — mentioned generally as an option for anyone not ready to manage a profile themselves, not applied to the protagonist directly, to avoid implying the reader herself needs it.
- **The Connector role and its referral tiers** (PRD-01) — used as the protagonist's son's path to help without taking over.
- **The two Level 1 ID verification paths** (PRD-05/14/20) — self-service ~2-minute phone flow and the video-call fallback with a live reviewer, used as the protagonist's chosen path.
- **Field-level privacy tiers and the Blurred/Public photo option** (PRD-02) — used directly in the "easing back in" section.
- **Biodata Import** (PRD-02) — used directly, tied to an old typed/scanned biodata document.
- **No-subscription, free-to-join pricing model** — used in the "free senior dating sites" section to contrast with subscription-gated mainstream competitors.
- Verification-gate framing follows the SL#010–014 resolution: search, Discover, messaging, and private access requests require Level 1 ID Verification; profile creation/sharing/Biodata Import/privacy controls stay free and ungated.

## Protagonist

Margaret, 63, widowed three years, hypothetical and explicitly illustrative. Her adult son Daniel helps as a Connector. New name, not reused from articles #1–#14 (which used Farida, Sarah, Ryan, Nasrin, Rafiq, Nasima, Imran, Priya, Amara, Hana, Tania, Claire). Chosen per `context/brand-voice.md`'s Visual Representation guidance for broader international representation rather than defaulting to a South Asian name.

## Internal Links / Related Posts

Outbound network access to connect.panosia.com was blocked this session (`EGRESS_BLOCKED`), consistent with the documented gap in `MEMORY.md`'s "Gaps To Resolve" section for cloud/scheduled sessions. Per that file's fallback policy, no fresh sitemap fetch was attempted. Reused these URLs, already confirmed live in recent runs (SL#010, #012, #013, #014):

- https://connect.panosia.com/posts/how-to-find-a-life-partner
- https://connect.panosia.com/posts/what-is-a-connector-and-why-it-matters
- https://connect.panosia.com/posts/getting-started-on-panosia-connect-build-trust-and-get-discovered
- https://connect.panosia.com/posts/self-service-identity-verification-feature-launch

The chat-messaging feature-launch post (`app-chat-messaging-feature`) was considered but left out of both the in-body links and Related Posts, since messaging mechanics are not a central focus of this piece; it can be added back if a reviewer finds a natural fit.

**Re-verify all four links against a live sitemap fetch before publishing.**

## Open Items / Assumptions Flagged for Human Review

- No pre-draft check-in was possible (automated cloud routine run); outline and angle decisions were made using this brief plus editorial judgment. Flagging here per the task instructions instead of blocking on human input.
- Keyword is OpenSEO-validated per the brief (no bn-first scope gap flagged, unlike SL#005/006/007/012).
- Fact-checked and `seo-reviewer`-reviewed 2026-09-23 (verdict: publish after required fixes, all applied): fact-check fixed a verification-gate phrasing contradiction and an incomplete "Hidden" privacy tier description; review fixed a meta-description truncation bug, cut a duplicated "No Subscription, Ever" section restating the pricing point already covered earlier, added first-use plain-language glosses for "Discover" and "biodata," and fixed two delayed-subject sentences (the intro and the Biodata Import section) for ESL readability. Status: publish-ready (en).
- Internal links need re-verification against a live sitemap before publishing (see above).
