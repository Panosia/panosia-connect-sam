# Research Brief — SL#020

Source: Notion Blog Posts DB, "How to Import Your Profile from LinkedIn (and What Panosia Does With It)" (Priority 17), from the "Sep Blog Posts: Plan" raw ideas checklist ("How to import from LinkedIn (Auto rich text)"), confirmed genuinely new 2026-09-12.

**Core thesis**: A practical feature walkthrough — how LinkedIn profile import works, what it fills in automatically, and what a Candidate should still review or edit before sharing (a career profile and a matrimony profile serve different purposes, even when some fields overlap).

**Reader**: A new or prospective Candidate who wants to create a profile quickly and has heard about, or wants, a way to reuse their existing LinkedIn profile.

**Angle**: Step-by-step feature explainer, plus the "what to still customize" caveat so it doesn't read as "just copy your resume."

**Confidence flag (as logged in Notion)**: "Needs a keyword check before drafting - not yet researched (this is a specific product feature, likely lower search volume than persona-level content, worth a quick keyword-metrics check rather than a full research pass)." No OpenSEO/DataForSEO keyword data exists for this topic; `context/target-keywords.md` has no matching entry. Primary keyword below is an editorial best guess for the feature-explainer intent, not volume-verified.

**Important mechanic correction made during this run (2026-09-28)**: the brief's phrasing ("LinkedIn profile import," "LinkedIn Import") reads as if Panosia Connect has a dedicated LinkedIn OAuth/API integration. It does not. The real, fact-checked mechanic (confirmed in `posts/004-getting-started-on-panosia-connect/en/004-article.md`, lines 39-45, and now added to `context/site-profile.md`'s Biodata Import bullet) is: LinkedIn's own "Save to PDF" profile export → upload that PDF through the same AI-assisted Biodata Import tool used for any biodata document (or paste the copied LinkedIn profile text directly). There is no separate "Connect LinkedIn" button or live sync. This draft must describe it that way, reusing Biodata Import with a LinkedIn-sourced document, not as its own distinct feature. This avoids the risk (flagged during this run's initial pass) of inventing a nonexistent LinkedIn integration.

**Grounding mechanics** (from `context/site-profile.md`):
- Biodata Import (AI-assisted): extracts and pre-fills profile fields (name, DOB, religion, nationality, height, marital status, languages, location, education, occupation, family details, about-me), each field flagged with a confidence indicator, always reviewed before accepting.
- The LinkedIn path specifically: LinkedIn → "Save to PDF" → upload to Biodata/Profile Import (or paste text). Free, no verification required.
- Field-level privacy (Public / Privately Shared / Hidden) applies to every imported field, same as any manually entered field — importing doesn't bypass privacy controls.
- A career profile and a matrimony profile differ in what should stay, what needs editing, and what a LinkedIn import naturally leaves out: family background, religion, marital status details, an "About Me" written for a partner search rather than a recruiter, and privacy choices LinkedIn has no equivalent of.
- Free forever: profile creation and Biodata Import/Export carry no verification requirement and no cost.

**Avoid duplicating**: article #4's own "Step 1" already covers Biodata Import briefly, including the LinkedIn-via-PDF path in two sentences. This SL#020 piece should go deeper specifically on the LinkedIn angle (why reuse it, exactly how, and what to change afterward) rather than repeating #4's full seven-step onboarding walkthrough.
