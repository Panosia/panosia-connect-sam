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

Sourced from the live app's homepage (`panosia-connect/src/pages/HomePage.tsx` + `home.json`, sibling repo; last refreshed 2026-08-26). This homepage gets restructured often, re-verify before trusting a stale claim below.

- Profile Import: AI import from a PDF/DOC/image biodata or LinkedIn profile, auto-fills fields, user confirms. Free.
- Profile Export: download profile as a formatted biodata PDF anytime, pick a theme, choose what's included. Free.
- Profile Multi-View: Public View (limited, default for every visitor) vs. Private View (full, visitor requests access, owner approves/rejects per visitor).
- Field-level privacy: fields like name/photo can be shown full/blurred/hidden or full/initials-only.
- Search/Discover filters: gender, age, marital status, verification status, country/state/city, candidate type. No longer has its own homepage marketing section.
- Shareable profile link, not a PDF: link previews (e.g. WhatsApp) respect the visitor's granted privacy level. Homepage's "Old Way vs. Panosia Connect Way" comparison currently covers 2 contrasts: Contact Info and Verification.
- Managed Profiles: a verified member/guardian can create and manage a full profile for someone not on the platform: import their biodata, draft, admin review, publish with a "Managed" badge, message on their behalf once live.
- Verification ladder, all optional/pay-per-use, none required to join: Level 1 ID Verification (photo ID + selfie + face scan, unlocks search/discover/full-profile requests/chat), Level 2 Background Check (live video call reviewing personal/education/work history, either side can request once real conversation has started), Level 3 In-Person Verification (local verifier confirms the profile in person; "Become a Verifier" path exists). Each gives a private shareable report. Credit history and criminal history checks are "coming soon," not live.
- Verification References: candidate lists real people who know them; visitors can message references directly.
- Family Tree & Social Connections: visible once a visitor is granted full/private access.
- Connector role: family/friends/community who vouch and facilitate rather than search themselves. Current marketing personas: Family (parent/sibling/cousin), Friend or Colleague, Religious/Community Leader. What a Connector can do: be a reference, join a family tree, share a profile, explore/browse candidates. Separate own-privacy reassurance: staying off public search, pausing/deleting your own account anytime.
- Secure Chat: message a candidate directly, message their references first, message family/friends once granted private access, no phone/email required upfront.
- Pricing: free forever (profile creation, discovery & sharing, privacy controls, family features, biodata PDF generation), no subscriptions. Only paid products: the verification services above, pay-per-use.
- Brand microcopy worth reusing: "Free Forever" / "No Subscription"; "not a dating app," now phrased as "for people seriously seeking marriage."
- Not currently on the homepage, may still be accurate elsewhere, re-verify before citing as homepage content: a dedicated Discover/search section, a "How It Works" video section, a Trust & Transparency section (Report/Block/GDPR/bank-grade), the fuller multi-paragraph About Us founding story (see `## Notes` below), and most of the old blog teaser list.

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
