# Research Brief — SL#006: Biodata for Marriage Positioning

Source: Notion Blog Posts DB row "Your Biodata Is Already Done Here: Skip the Separate Biodata Maker" (SL#6, Priority 3, Persona: Protective Parent/Family), drafted into this repo by the "Daily Blog Draft" automated routine, 2026-09-14.

## Research Brief (from Notion)

Positioning piece against a newly-discovered competitive category.

**Primary keyword:** biodata for marriage — real tracked demand; category currently dominated by 6 standalone biodata-PDF tools (biodatamaker.app #1, biodataformarriage.net, marriagebiodata.ai, marriagebiodataonline.com, freebiodatamaker.com, biodatabanao.com), per 2026-09-12 OpenSEO competitor research.

**Core thesis:** Parents/families searching "biodata for marriage" are reaching for a single-purpose PDF tool to solve one step, when Panosia Connect's own Profile Export feature already does that step and connects it to everything after (privacy controls, sharing, verification, Connector network), so there's no need for a separate, disconnected tool.

**Reader:** A parent or family member tasked with preparing a biodata, who doesn't yet see Panosia Connect as relevant to that specific task.

**Angle:** "Do the biodata step here, then everything else" — walk through creating a biodata/profile export on Panosia Connect as the practical answer to the biodata-tool search, then show what it unlocks beyond a standalone PDF.

**Avoid:** Turning this into a generic platform pitch — stay anchored on the concrete biodata task first.

Source: OpenSEO Market Competitors research, 2026-09-12 (Biodata Maker category notes).

## Keyword Clustering Findings (2026-09-12)

A real, sizeable Bengali/Muslim-specific angle for this topic surfaced: "মুসলিম বিয়ের বায়োডাটা pdf" (1,000/mo) and "বিয়ের বায়োডাটা ফরমাট" (590/mo), combined ~1,590/mo, not yet reflected in the original English-only brief. Recommend either drafting this as a bilingual piece from the start, or treating a bn version as a priority follow-up once the English draft ships, since the Bengali/Muslim biodata-PDF search demand is real and distinct from the generic English "biodata for marriage" term this brief was originally built around.

**Confidence note:** this brief cites specific search volumes and named sources (OpenSEO/DataForSEO competitor research and keyword clustering, both dated 2026-09-12), matching `context/target-keywords.md`'s "Verified Keywords" entry for "biodata for marriage." Treated as fully OpenSEO-validated, not a lower-confidence/unvalidated topic — no WebSearch sanity check was required or run per the routine's Step 3 rule.

## Scope note carried into the draft

Like SL#005 (দ্বীনদার পার্টনার), this routine produces an English-only draft. The Bengali/Muslim-specific biodata-PDF demand (~1,590/mo combined) is real and distinct from the English "biodata for marriage" term this English draft targets. A dedicated bn piece (via `bn-translator` or a fresh bn-first session, written to lead naturally with বিয়ের বায়োডাটা ফরমাট / মুসলিম বিয়ের বায়োডাটা pdf rather than a literal translation) is still needed to actually capture that Bengali demand. Flagged in-file at the top of the en draft and here.

## Internal links / sitemap note

Outbound network access was blocked in this run (`EGRESS_BLOCKED` fetching `https://connect.panosia.com/sitemap-posts.xml`), consistent with the known Cloud/scheduled-sessions gap logged in `MEMORY.md`. Per that fallback, internal links and the Related Posts section below reuse slugs already confirmed live elsewhere in this repo (articles #3 and #5 both re-confirmed these against the sitemap on 2026-09-12/13):

- https://connect.panosia.com/posts/how-to-find-a-life-partner
- https://connect.panosia.com/posts/what-is-a-connector-and-why-it-matters
- https://connect.panosia.com/posts/getting-started-on-panosia-connect-build-trust-and-get-discovered
- https://connect.panosia.com/posts/self-service-identity-verification-feature-launch

Re-verify against a fresh sitemap fetch before publishing, per the standing MEMORY.md gap note.

## Product mechanics to ground the piece (from `context/site-profile.md`, PRD-02)

- **Biodata Import (AI-assisted):** upload an existing biodata document (PDF, DOC, or even a photographed/scanned page) and the system extracts and pre-fills profile fields, each with a confidence indicator for the user to review before accepting. Directly useful for a family with an old typed or paper biodata.
- **Biodata Export (PDF):** pick a visual theme, pick the privacy level for that specific document (a copy for a stranger can be Public-fields-only while a copy for family includes more), generate, download. Free, no verification needed.
- Field-level privacy (Public / Privately Shared / Hidden per field) applies to the exported biodata too, so the same profile can produce different biodata documents for different audiences, something a static PDF tool cannot do.
- Beyond the PDF: the same profile plugs into Discovery, the Connector network, Verification, and Private Access Requests, the standalone tools stop at the PDF.
