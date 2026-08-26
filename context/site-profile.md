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

Extracted from the live app's homepage (`panosia-connect/src/pages/HomePage.tsx` + `src/i18n/locales/en/home.json`, a sibling repo to this one; last refreshed 2026-08-26 against commit `92fc716a`, "update landing page," which trimmed and restructured several sections vs. the version this was first written from). Use this for feature-accurate detail instead of guessing at product mechanics; re-verify against that source if a claim here might be stale, this homepage gets restructured fairly often.

- Profile Import: AI-powered import from a PDF/DOC/image biodata or a LinkedIn profile; auto-fills profile fields, user reviews and confirms. Free.
- Profile Export: download the profile as a formatted biodata PDF anytime, pick a theme, choose what's included (public-only up to full profile). Free.
- Profile Multi-View: one profile, two views. Public View (limited info) is what every visitor sees by default; Private View (full info) requires the visitor to request access and the owner to approve or reject, per visitor. No duplicate profiles to maintain.
- Field-level privacy: fields like name and photo can be shown as full/blurred/hidden or full/initials-only; framed on the homepage as "you control who sees what."
- Search/Discover filters (still real app functionality: gender, age range, marital status, verification status, country, state, city, candidate type), but the homepage's own dedicated "Search Candidates, Near You or Across the World" marketing section was removed in the 2026-08-24 update, don't cite it as a current homepage section.
- Shareable profile link (not a PDF): link previews (e.g. in WhatsApp) respect the visitor's own granted privacy level, not a static export. The homepage's "Old Way vs. Panosia Connect Way" comparison was trimmed to 2 rows (from 4): Contact Info (private until granted vs. exposed/sold to strangers) and Verification (provable identity + trust badge vs. no way to know who's real); the Sensitive Info and Your Data rows were cut as redundant with Contact Info.
- Managed Profiles: a verified member, homepage copy now says "a verified member and guardian," can create and manage a full profile for someone not on the platform themselves: import their biodata, draft, submit for admin review, publish with a visible "Managed" badge, and message on the profile's behalf once live. (The "identity fields lock after approval" detail was dropped from homepage copy in the 2026-08-24 update; may still be true in-app, just not currently stated there.)
- Verification ladder, all optional and pay-per-use, none required to join:
  - Level 1, ID Verification: photo ID + selfie + face scan from the phone; confirms name/DOB/gender/location/face; unlocks search/discover/full-profile requests/chat; gives a private shareable report.
  - Level 2, Background Check: a live video call reviewing personal info, education, and work history; either side can request it once real conversation has started; notified by email + in-app; private shareable report.
  - Level 3, In-Person Verification: a local verifier meets the candidate in person and confirms the profile is accurate; same request/notify flow as Level 2; a "Become a Verifier" path exists for locals who want to do this.
  - Credit history check and criminal history check are both listed as "coming soon" in pricing, still not live, don't write about them as available.
- Verification References: a candidate lists real people who personally know them; visitors can message those references directly to build trust before contacting the candidate.
- Family Tree & Social Connections: a candidate's family and wider social connections (friends, colleagues) can appear on their profile once a visitor is granted full/private access, to help evaluate roots and authenticity.
- Connector role: family/friends/community members who vouch and facilitate rather than search for themselves. As of the 2026-08-24 update the marketing personas were consolidated from 6 down to 3, "Family: Parent, Sibling, or Cousin," "Friend or Colleague," and "A Religious or Community Leader" (each still names every original relation in its body copy, so nothing is actually lost, just regrouped). What a Connector can do (4 cards): be a reference, join a candidate's family tree as a known relation, share a candidate's profile into their own network, explore/browse candidates. A separate 2-card "worried about your own privacy" reassurance pairing covers staying off public search and pausing/deleting your own account anytime, placed right where someone is deciding whether to join as a Connector.
- Secure Chat: message a candidate directly from their profile, message their verification references first, and, once granted private access, message their family/friends too. (The explicit "share your phone/email only when you're ready" line was dropped from homepage copy in the 2026-08-24 update; the no-phone/no-email-to-strangers framing is still the section's title.)
- Pricing: platform is free forever (profile creation, discovery & sharing, privacy controls, family involvement features, biodata PDF generation), no subscriptions, no hidden fees. Only paid products are the verification services above, pay-per-use. The "30-day money-back guarantee" line was removed from homepage pricing copy in the 2026-08-24 update, don't cite it as current homepage messaging without reconfirming it's still offered.
- Recurring brand microcopy worth reusing: "Free Forever" / "No Subscription" framing; "not a dating app" reassurance (now phrased as "for people seriously seeking marriage," not "lifelong commitment").
- Sections present as of 2026-08-15 but removed from the homepage by the 2026-08-24 update: a "How Panosia Connect Works" video section, and a dedicated Trust & Transparency section (bank-grade security / GDPR / Report / Block / Pause / Delete framing). Report and Block are no longer surfaced anywhere on the current homepage; Pause/Delete now only appears inside the Connector privacy-reassurance pairing above. The About Us section was also cut way down, from a multi-paragraph founding story (mission, vision, "LinkedIn of matrimony" ambition, Charlotte location, "Read Our Story"/founder-story links) to just the title, one opening line ("Not because the market needed another app."), and the founding date; those fuller facts (see `## Notes` below) may still be accurate and still live on the dedicated About page or founder-story blog post, just no longer stated on the homepage itself. The homepage's blog teaser also dropped from 6 linked posts to 3 (kept: "Getting Started on Panosia Connect," "Why Did We Create Panosia Connect?," "Why the Name Is Panosia Connect"; dropped: the job-search-analogy post, the 3-problems-families-face post, and article #1 of this repo's own series). Don't reference any of these removed sections as current homepage content; the underlying app features they described may still exist, but re-verify before citing them as homepage messaging.

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
