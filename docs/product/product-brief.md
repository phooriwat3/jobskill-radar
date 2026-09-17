# Product Brief

Status: Draft - WP-01 source of truth
Date: 2026-09-17
Owner role: Product owner (individual not yet assigned)

## Value proposition

JobSkillRadar helps an individual job seeker build a private, evidence-backed
view of recurring qualifications across job advertisements. A user captures
only content they are already viewing, reviews the proposed capture, keeps
the original evidence unchanged, and sees deterministic Thai/English
qualification signals that can be corrected without rewriting the source.

The smallest useful product is local-first: it works without an account,
cloud synchronization, external AI, or a server retrieving source URLs.

The analysis contract is fixed across the product documents: analysis uses
exactly the immutable job-text value accepted when the job is saved. Evidence
uses zero-based, end-exclusive offsets into the exact UTF-8 bytes plus their
SHA-256 source digest. Later metadata edits, including URL/title changes,
notes, collections, and corrections, are not analysis input.

## Users and hypotheses

The following personas are hypotheses until representative user evidence is
recorded. They are planning inputs, not validated market claims.

### P-01: Individual job seeker

Needs a private way to compare recurring qualifications without manually
re-reading every advertisement.

Journey: view a job page -> invoke capture -> inspect and edit the preview ->
save locally -> inspect extracted qualifications and evidence -> correct
results -> group and compare jobs -> export or delete.

### P-02: Bilingual job seeker

Needs Thai and English surface forms to map consistently while retaining
source wording and distinctions such as Java versus JavaScript.

Journey: capture mixed-language advertisements -> inspect canonical terms and
aliases -> review uncertain mappings -> correct or remap them -> compare
unique-per-job frequencies.

### P-03: Privacy-conscious user

Needs a clear answer to what is stored, where it is stored, whether it is
transmitted, and how it is deleted.

Journey: review the capture preview -> use the local-only MVP -> export a
backup -> delete a job or all local data -> verify that no account,
telemetry, or cloud transmission is required.

### P-04: Maintainer/analyst

Needs versioned requirements, ontology, corpus, evaluation output, and
decisions so changes can be reviewed and reproduced.

Journey: propose a requirement or ontology change -> link evidence, risk, and
ADR -> update permitted corpus material if needed -> run deterministic
evaluation -> review regressions -> approve or reject the change.

### J-05: Manual fallback capture

When page extraction is unavailable or incomplete, the user selects the
relevant text if possible, or chooses the manual-paste fallback and supplies
only the intended job-ad text. The user reviews the proposed title, source
metadata, and job text, removes unrelated content, saves the capture, and
then inspects evidence-backed analysis. The product does not fetch the source
URL to fill the gap, and the fallback remains available when the page
structure changes.

### J-06: Accessible evidence and data-control journey

A keyboard-only or assistive-technology user invokes capture, moves through
the preview with visible focus and programmatic labels, reviews source
evidence, confidence, and correction states without relying on color, and
completes save, comparison, export, and deletion. The same journey is tested
at the approved zoom/reflow sizes with Thai, English, mixed-language, and
long-token content. Any missing target or matrix is an open WP-02 decision,
not an accessibility claim.

## MVP boundary

### Included

- Explicit user action starts capture.
- Page-derived content where available, selected text, and manual paste.
- Inspectable preview and editing before save.
- Immutable original evidence with separate edits, analysis, and corrections.
- Local versioned storage, collections, duplicate warnings, filtering, and
  comparison.
- Deterministic bilingual qualification analysis with evidence links,
  confidence meaning, and unique-per-job frequency.
- User accept/reject/add/remap corrections without altering original evidence.
- JSON and CSV export, individual/all-data deletion, and offline operation.
- Export is the MVP data boundary; import/interchange behavior and
  invalid-import testing are deferred unless separately approved and added
  by an ADR/change record.
- Planned security, accessibility, and accuracy verification.

### Deferred

- WP-06 optional authenticated synchronization and its backend.
- WP-07 opt-in AI assistance with deterministic fallback.
- WP-08 operational hardening and release automation.
- WP-09 representative real-world validation and distribution preparation.
- PDF export, additional site adapters, and document upload after separate
  approval.

### Non-goals

- Mass or unattended crawling, scheduled scraping, or backend URL fetching.
- Bypassing authentication, paywalls, CAPTCHAs, robots controls, or other
  access restrictions.
- Automatic applications, ATS/recruitment workflows, salary prediction, or
  applicant scoring.
- Credential, private-message, or unrelated browsing-data collection.
- Antivirus or malware-detection claims.
- Perfect, exhaustive, or universally representative extraction claims.
- Native mobile applications or premature microservices.

## Assumptions to validate

| ID | Assumption | Evidence owner | Current state |
|---|---|---|---|
| A1 | Local anonymous usage provides enough first-release value. | Product owner | Unknown |
| A2 | Capture is user-initiated from content the user may view. | Product/privacy owners | Proposed |
| A3 | Local retention of source URL/title and accepted text is acceptable. | Privacy owner | Unknown |
| A4 | Governed deterministic rules can provide a useful Thai/English baseline. | Analysis/evaluation owners | Unknown |
| A5 | Chrome and Edge share sufficient MV3 behavior for the initial design. | Architecture/extension owners | Unknown |
| A6 | Selection and paste are acceptable fallbacks when extraction fails. | Product/extension owners | Unknown |
| A7 | A local dashboard can use the same dataset without a backend. | Architecture owner | Proposed |

## Constraints

- The MVP must not require network access, an account, cloud sync, or AI.
- Original evidence must remain distinct from derived analysis and corrections.
- Source URLs are references and must not be fetched by a backend.
- Page and user text is untrusted at every boundary.
- Corpus examples require provenance, permission, minimization, and
  annotation governance before repository inclusion.
- Performance, supported browser versions, release distribution, and
  accessibility target remain evidence-backed decisions for later packages.

## Success evidence

WP-01 does not claim product success or implementation. Later packages must
show, at minimum, an offline end-to-end journey, evidence traceability,
correction isolation, deletion behavior, deterministic repeatability,
accessibility evidence, and bilingual accuracy results from a governed
corpus. Targets must be approved only after baseline measurement.
