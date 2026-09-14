# Site Profile

Use this file for company, audience, and offer context.

## Company

- Name: Panosia Connect (by Panosia LLC)
- Website: https://connect.panosia.com
- Product or service: Marriage/matchmaking platform built on trust-based, community-driven introductions
- Main offer: Free-to-join international matrimony platform ("No Subscription"). Candidates create profiles and search for a life partner; Connectors vouch for people and facilitate introductions. Only paid products are optional one-time verification services: Level-1 ID Verification, Level-2 Digital Background Check, Level-3 In-Person Verification.

## Audience

- Primary audience: Adults seeking a life partner for marriage (Candidates); Bangladesh is the primary Bengali-language market, with Bangladeshi diaspora communities as a close secondary and some West Bengal reach
- Secondary audience: Connectors — parents, siblings, relatives, trusted friends, professional matchmakers, religious/community organizations
- Jobs to be done: Find a suitable, genuine life partner through trusted channels; involve family in the search; verify someone's identity before serious discussions; avoid scams and misrepresentation
- Biggest objections: "Why pay for matchmaking when job search is free?"; fear of fake profiles and fraud; privacy concerns about sharing family details; skepticism that online matrimony can replace family-led introductions

## Content Goals

- Main acquisition goal: Organic traffic for matrimony/matchmaking and trust-safety queries in English and Bengali
- Main conversion goal: Signup and profile creation; Connector participation; network growth; optional verification purchases (one-time, not subscription)
- Priority content types: How-it-works and product explainers, trust & safety content, feature announcements, matchmaking guidance, cultural/community content, FAQ/support
- Topics to avoid: Member data or individual stories without permission; legal claims about marriage/divorce law; guaranteed-match promises; anything that undermines the trust-first positioning

## Differentiators

- Connector model: family/friends/community are participants, not just candidates ("community before algorithms")
- Visible real relationships: connections shown with context (father, cousin, colleague) rather than anonymous browsing
- No-subscription model: core platform free forever; monetization via optional one-time verification services (ID Verification, Digital Background Check, In-Person Verification)
- Professional verification ladder: live video session, government ID + face match, locked verified details, PDF verification report
- Privacy-first controls: user decides what's public, approval-based access, revocable at any time
- Principles: identity before interaction, privacy before exposure, community before algorithms

## Product Features

**Primary source (2026-09-13): the code-verified PRDs in the sibling repo `panosia-connect/docs/prd/*.md`** (each PRD stamped "Code-verified: 2026-08-02"). These describe actual shipped mechanics in far more concrete detail than the homepage, and are the preferred source for anything an article needs to explain precisely (a specific flow, a specific limit, a specific button). The homepage summary below (`panosia-connect/src/pages/HomePage.tsx` + `home.json`, last refreshed 2026-08-26) is the marketing-message layer on top and still useful for framing/headlines, but re-verify against the PRDs before citing a mechanic as fact. PRDs are numbered; cite by number in research notes (e.g. "PRD-03") so a later refresh can find the source fast. Landing page structure/messaging itself is PRD-10.

Use this section to ground articles in a specific, real mechanic rather than a generic platform mention — "field-level privacy lets you set your phone number to Privately Shared while keeping your name public" reads as promotion that's actually useful; "the platform protects your privacy" does not.

### Profiles & Privacy (PRD-02)

- A profile has 8 sections: Identity, Personal Details (height, religion, nationality, ethnicity, marital status, mother tongue, languages, hobbies), Family Details (free text), Location, Education, Professional, Contact (phone + optional social links), About Me.
- **Field-level privacy, three tiers per field** (and per photo): Public, Privately Shared (visible only to someone granted private access), Hidden (owner + staff only). Changeable inline while editing, no separate save step. A dedicated Privacy Settings screen lets someone review/change every field at once, grouped by section, plus bulk actions (set everything Public/Privately Shared/Hidden, or reset to a "candidate" vs. "connector/helper" default template).
- The profile photo has a specific "Blurred / Public" option: publish a softly blurred version publicly while keeping the sharp original gated, reversible anytime — a concrete answer to "I don't want my photo searchable but still want a profile."
- Photos: profile photo, cover photo, gallery capped at 6, each with its own independent privacy setting; drag-and-drop upload with automatic compression.
- **Biodata Import (AI-assisted)**: upload an existing biodata document — PDF, DOC, or even a photographed/scanned page — and the system extracts and pre-fills fields (name, DOB, religion, nationality, height, marital status, languages, location, education, occupation, family details, about-me) each with a confidence indicator, for the user to review before accepting. Genuinely useful for someone with an old typed or paper biodata, or an older relative less comfortable typing everything from scratch.
- **Biodata Export (PDF)**: pick a visual theme, pick the privacy level for that specific document (so a copy for a stranger can be Public-fields-only while a copy for family includes more), generate, download. Free, no verification needed.
- Onboarding is a mandatory 5-step wizard (role → photo → basic identity/location → marital status → phone) before a new member reaches the rest of the app; none of the 5 steps are skippable. Privacy defaults are seeded automatically from the role answer (Candidate vs. Connector), not a separate wizard step.

### Discovery & Matching (PRD-03)

- Discovery isn't one big public feed; it centers on networks. Tabs: My Connections, My Shortlist, My Referrals, My Followers, Browse All Profiles (full directory, gated by verification or the trial window below), and Look up by exact email.
- **"Browse someone's network"**: every profile card has a Network button — click it to see who that person has connected with, shortlisted, or been followed by, the same three-way view (network/referrals/followers) they'd see of their own. This requires the *browsing* member to be ID-verified. It's one hop at a time, not an automated friend-of-friend engine — a concrete, honest way to describe "see who vouches for who" without overclaiming an algorithm.
- Filters: gender, marital status, age range, religion/ethnicity (include-only or exclude modes), city/state/country (free text supported), verification status, candidate status.
- **Connect → Shortlist**: adding someone to your network is a light "Connect" bookmark first, then an optional "Shortlist" promotion once connected, marking them a serious prospect. Shortlisting is also what unlocks sending a private access request to that profile.
- **Compatibility score**: a real, shipped 0-100 percentage shown on profile cards, from a fixed weighted formula — age closeness (heaviest weight), same city/country, education closeness, religion match — only computed once both people have entered a birth date. Honest framing for articles: this is a straightforward compatibility calculator, not AI/ML matching and not a stand-in for family judgment.
- Saved searches: default one-tap presets (Posts, My Connections, My Shortlist, Female/Male Candidates, etc.) plus a member's own custom saved filter combos.
- A member's own Connections/Referrals/Followers views each have a shareable link.

### Private Access Requests (PRD-04)

- The mechanism behind "ask before you see the private stuff": a "Request Private Access" button appears whenever private info is hidden from the current viewer.
- Requesters pick from message templates (serious matrimony interest, family introduction, mutual-connection referral, general interest, seeking referrals, connector/family-manager networking) or write a custom message, up to 500 characters.
- Rate-limited to 5 requests per rolling 24 hours, one active request per requester/profile pair at a time.
- Owner gets email + in-app/push notification, approves or declines (optionally with a short reply) from a two-tab dashboard (Received / Sent) at `/requests`, with live counts and status filters.
- Approval unlocks that specific requester's view of the "Privately Shared" fields immediately; it does not change anyone else's access. **Access can be revoked at any time** and takes effect immediately, and a revoked request can be re-sent later, restarting the cycle. This "ask, grant, and take back control anytime" loop is a strong, concrete answer to the "I don't want to lose control once I share something" objection.
- Sending a request does not itself require the sender to be verified (their verification status is just shown to the recipient for context) — worth knowing so an article doesn't overstate the verification gate here specifically.

### Trust & Verification (PRD-05, PRD-14, PRD-20)

- Verification is the single gate behind three things, and only these three: sending direct messages, requesting someone's private access, and browsing another member's network. It is not a search-ranking boost, and profile creation/sharing/export are never gated on it.
- **Confirmed by user (2026-09-13)**: verification (Level 1 ID Verification) is mandatory before requesting someone's private access, and before any interaction with another member, including chat. PRD-04's "sender doesn't need to be verified to send a request" note (in its "How This Differs From the Original Plan" section) does not reflect current product behavior — treat PRD-05's gate list (messaging, private access requests, network browsing) as authoritative over that specific PRD-04 line. Articles should state plainly that requesting private access requires verification, same as chat/messaging.
- **Two ways to complete ID verification**, same "Approved" badge either way: (1) a **self-service vendor check**, a guided ~2-minute document-plus-selfie flow done from a phone, no appointment needed (this is the concrete "how fast" detail worth naming in a feature explainer); or (2) a **video call fallback** with a live reviewer, for documents the automated check can't handle or for someone who'd rather talk to a person.
- Statuses a member can track themselves: Pending, Scheduled, In Review, Approved, Rejected (with a reason and an invite to retry), Expired.
- Once approved, **first name, last name, date of birth, and gender lock** and can no longer be edited — a specific, concrete anti-fraud detail ("a verified identity can't quietly drift") that's more persuasive than a vague "we verify people" claim.
- Verification produces a **downloadable report**, visible to the profile owner and to anyone they've separately granted private access to, gated behind a legal-disclaimer acknowledgment — never public.
- Level 2 (Digital Background Check: live video review of personal/education/work history) is a separate optional add-on layer, does not itself unlock messaging/access/network browsing. Level 3 (In-Person Verification) is shown on the pricing page as "Coming Soon" — not actually purchasable yet, so don't describe it as live.
- No family-initiated verification of someone else (except a guardian verifying on behalf of a Managed Profile candidate, see below); no peer/community vouching that substitutes for ID verification itself (community vouching lives in the Social Map's relationship-tag voting, a separate signal, see below).

### Social Map / Family Tree (PRD-09)

- A visible family tree on a profile: tag existing platform members as father, mother, spouse, children, siblings, extended family, or social/professional ties (friend, colleague, mentor). It reuses the existing connections system, not a separate database — a family tree is just a person's connections with relationship tags attached.
- **Community voting on individual relationship claims**: anyone with private access to the profile can upvote or downvote a specific tag (e.g., confirm or dispute "this is her brother"), shown as a running "+N"/"-N" score per tag. This is a genuinely distinctive, concrete trust mechanic worth naming directly — it's not just "family involvement," it's "other people who know the family can vouch for or flag a specific claimed relationship."
- Profile owners never vote on their own tree (they get manage/edit controls instead) — the design deliberately separates "who manages the claim" from "who certifies it."
- Fully gated behind the same private-access system as other protected fields: no private access, no visible tree at all (a locked placeholder, not a partial one).

### Connector Role & Managed Profiles (PRD-01, PRD-19)

- **Connector** is the platform's own term for anyone helping someone else search rather than searching themselves: parent, sibling, friend, colleague, or religious/community leader. It's a toggle on the same account type, not a separate product tier — someone can be a Candidate today and switch to Connector mode once they're married, still using their same network. Referral/reputation tiers exist for Connectors: Connector → Regional Connector (10 referrals) → Community Leader (50 referrals), shown as a badge/count on the profile.
- **Managed Profiles**: a verified member (parent, sibling, relative, trusted Connector) can create and fully manage a profile for a candidate who has no account of their own — filling in their details, uploading their photos, importing their biodata, and submitting it through the same verification review queue as a self-managed profile, including at least one reference (the guardian themselves counts). Every managed profile carries a visible "Managed" badge and a "Managed by [Guardian Name]" link; interested members contact the guardian, not the candidate, through standard messaging. Live for 6 months once approved, then expires out of discovery (data preserved, re-submittable). This is the concrete answer to "my parent/relative isn't ready to be online themselves" — a real, named feature, not just "family can help."

### Messaging (PRD-23)

- Two distinct paths, both gated on the sender holding approved ID verification: **Chat** (real-time, in-app, read state, a standing on-screen safety reminder, Report button built into every thread) and **Email** (one-off message delivered by actual email; the recipient can only reply by visiting their own Panosia Connect profile, not by hitting reply — the sender's email address is never exposed).
- If the person being messaged isn't verified yet, the Chat button still works: it offers to send them a one-tap nudge to get verified, rather than a dead end.
- No group chat, no file/photo attachments, no automated content moderation — safety runs on the member-driven Report flow instead. Worth stating plainly in a trust/safety article rather than implying more automated moderation than exists.
- Three distinct delete options exist (delete one message for everyone, wipe an entire conversation for both sides, or remove a conversation from just your own inbox) — a concrete, specific answer to "can I take something back."

### Platform Experience (PRD-06)

- Installable as a Progressive Web App (adds to phone/desktop home screen, opens without browser chrome) — offered to engaged signed-in users after a couple of visits, not on first load.
- Bilingual throughout (English and Bangla), not just on marketing pages.
- Named visual themes (e.g. Navy, Light, Dark, Sunset, Emerald, Ocean), saved to the account and synced across devices — there's no auto light/dark-matching mode, so don't claim one.

### Pricing & Positioning

- Free forever: profile creation, Profile Import/Export, all privacy controls, discovery/search, connections, shortlisting, the Family Tree, Managed Profiles, messaging (once ID-verified). No subscription tier exists anywhere in the product.
- The only paid products are the optional verification services (Level 1 ID Verification live; Level 2 Background Check live; Level 3 In-Person Verification "Coming Soon," not purchasable), priced pay-per-use with a 30-day money-back guarantee mentioned on the pricing section.
- Brand microcopy worth reusing: "Free Forever" / "No Subscription"; "not a dating app," phrased as "for people seriously seeking marriage."
- Landing-page framing worth borrowing directly for hooks/headlines (PRD-10): "Stop Sharing Biodata in WhatsApp Groups. Share a link. Keep your privacy intact." / "Know Exactly Who You're Meeting. Every profile verified. Every claim confirmed." / "See Beyond the Bio. Discover Candidate's Roots, Their Values, Their Story." / "You're already married but want to help others? Become a Connector."

## Notes

- Founded November 2025 in North Carolina; founder-led, small team of engineers. Positioning tagline: "International Matrimony, No Subscription." Ambition: "the LinkedIn of matrimony."
- Mission: "To create a platform where candidates, families, and service providers come together to deliver every matrimony need — with trust at the center."
- Vision: "A future where every profile is authentic, every interaction is respectful, every match is built on trust, and every matrimony service is powered by the community."
- Core values: Integrity, Respect, Connection.
- Brand pillars (their framing): Community-Powered Matchmaking, Trust Through Verification, Complete Privacy Control, Focused on Marriage — not a dating app; built exclusively for serious, lifelong commitment.
- Bilingual site: English and Bengali (hreflang configured); new posts are typically published in both languages.
- Existing posts mix feature launches and educational content; posts use "Key Takeaways" boxes, recurring example personas (Sarah the Connector mother, Ryan the Candidate son), and clear H2 structure.
- Pricing model: free to join, no subscriptions ever; verification fees are one-time, billed via Stripe, with prices confirmed in-app before checkout.
- /support/guides/* educational pages are orphaned and slated to be rewritten as /posts/* content — a useful source of topic ideas.
