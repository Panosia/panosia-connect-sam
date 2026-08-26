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

Extracted from the live app's homepage (`panosia-connect/src/pages/HomePage.tsx` + `src/i18n/locales/en/home.json`, a sibling repo to this one, verified 2026-08-26). Use this for feature-accurate detail instead of guessing at product mechanics; re-verify against that source if a claim here might be stale.

- Profile Import: AI-powered import from a PDF/DOC/image biodata or a LinkedIn profile; auto-fills profile fields, user reviews and confirms. Free.
- Profile Export: download the profile as a formatted biodata PDF anytime, pick a theme, choose what's included (public-only up to full profile). Free.
- Profile Multi-View: one profile, two views. Public View (limited info) is what every visitor sees by default; Private View (full info) requires the visitor to request access and the owner to approve or reject, per visitor. No duplicate profiles to maintain.
- Field-level privacy: every field (name, photo, email, phone, DOB, gender, city, etc.) has its own visibility control, e.g. name can show full name or initials-only, photo can show full/blurred/hidden.
- Discover/search: filter by gender, age range, marital status, verification status, country, state, city, and candidate type.
- Shareable profile link (not a PDF): link previews (e.g. in WhatsApp) respect the visitor's own granted privacy level, not a static export.
- Managed Profiles: a verified member can create and manage a full profile for someone not on the platform themselves, import their biodata, draft it, submit for admin review, then publish with a visible "Managed" badge. Identity fields lock after approval; the manager can message on the profile's behalf.
- Verification ladder, all optional and pay-per-use, none required to join:
  - Level 1, ID Verification: photo ID + selfie + face scan from the phone; confirms name/DOB/gender/location/face; unlocks search/discover/full-profile requests/chat; gives a private shareable report.
  - Level 2, Background Check: a live video call reviewing personal info, education, and work history; either side can request it once real conversation has started; notified by email + in-app; private shareable report.
  - Level 3, In-Person Verification: a local verifier meets the candidate in person and confirms the profile is accurate; same request/notify flow as Level 2; a "Become a Verifier" path exists for locals who want to do this.
  - Credit history check and criminal history check are both listed as "coming soon," not live yet, don't write about them as available.
- Verification References: a candidate lists real people who personally know them; visitors can message those references directly to build trust before contacting the candidate.
- Family Tree: immediate family can join a candidate's profile as visible relations, shown to visitors once granted full/private access.
- Social Connections: beyond immediate family, relatives, friends, and colleagues can also appear as visible relations on a profile.
- Connector role: family/friends/community members who vouch and facilitate rather than search for themselves. Marketing personas used: a parent, a married sibling, a cousin abroad, a married friend, a colleague, a religious leader. What a Connector can do: explore/browse candidates, share a candidate's profile into their own network, join a candidate's family tree as a known relation, vouch as a reference, plus everything under Managed Profiles above.
- Privacy & safety controls: full per-field visibility control; family tree and social connections private by default and revocable anytime, one person at a time; Report (reason + evidence, reviewed by the Panosia team) and Block (blocked accounts are locked out, not just flagged) on any profile; a toggle to opt out of public search discoverability entirely; self-service pause (temporarily deactivate, reactivate anytime) or permanent delete of account and data. Copy also cites "bank-grade" encryption and GDPR-compliant data rights (export/correction/deletion).
- Secure Chat: message a candidate directly from their profile, message their verification references first, and, once granted private access, message their family/friends too, all without exchanging phone number or email until the user chooses to.
- Pricing: platform is free forever (profile creation, discovery & sharing, privacy controls, family involvement features, biodata PDF generation), no subscriptions, no hidden fees. Only paid products are the verification services above, pay-per-use, with a 30-day money-back guarantee.
- Recurring brand microcopy worth reusing: "Free Forever" / "No Subscription" framing; "not a dating app" reassurance (built for serious, lifelong-commitment marriage seekers); an "Old Way vs. Panosia Connect Way" contrast used for the private-link pitch (contact info exposed/sold vs. private until granted access; sensitive info stealable vs. controlled; no way to verify vs. provable identity + trust badge; permanent exposure vs. revocable one person at a time).

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
