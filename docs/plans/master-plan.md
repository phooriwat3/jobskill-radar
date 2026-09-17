# JobSkillRadar Master Plan

Status: Active - WP-01 approved; corrective review in progress
Repository path: C:\Projects\JobSkillRadar
Proposed product/repository slug: jobskill-radar
Date: 2026-09-17
Last repository inspection: 2026-09-17

## WP-01 approval record

WP-01 was approved for implementation by the user instruction recorded in
this Codex session on 2026-09-17. The repository does not record a named
approver; no person is invented here. The implementation baseline is commit
cd230e8, and the corrective work described in the WP-01 acceptance report is
the current uncommitted documentation change set.

## Current baseline

The original implementation-session inspection found an existing Git
repository at C:\Projects\JobSkillRadar, on branch main, with HEAD at
7eace60 (docs: add initial JobSkillRadar master plan). At the start of
the original WP-01 implementation, git status --short returned no changes.
That implementation was committed as cd230e8 (docs: implement WP-01
governance baseline). At the start of corrective implementation, commit
cd230e8 was checked out and git status --short again returned no changes.
The corrective changes are intentionally uncommitted until review.

The original tracked baseline contained these documentation files:

- docs/plans/master-plan.md
- docs/plans/wp-01-plan.md
- docs/prompts/wp-01/planning.md

No application source, package manifest, build configuration, CI workflow,
tests, ontology, corpus, ADR set, or risk register was observed before the
WP-01 documentation changes. WP-01 adds documentation and governance
artifacts only; it does not add product implementation, dependencies, or
infrastructure.

Tracked Markdown files were confirmed to be valid UTF-8 with LF line endings.
The earlier planning report's statements that the workspace had no Git
metadata and that the existing files were encoding-corrupted are historical
observations that are superseded by this inspection. The approved planning
report remains a planning record; current repository facts are recorded here
and in the WP-01 acceptance report.

The current post-correction git status --short is expected to list only the
documentation changes made by this corrective implementation. It must not be
described as a clean-worktree result until those changes are committed.

## Product scope

JobSkillRadar is a privacy-conscious tool for collecting a user's own
captures of job advertisements and comparing normalized qualifications across
jobs. Its central promise is evidence-backed analysis: every reported item
must be traceable to a captured job and an evidence snippet, while
deterministic analysis remains useful without an AI provider.

The initial architecture remains a proposed direction. It may contain a
browser extension, a local dashboard, independently testable analysis
packages, and a modular-monolith API reserved for a later synchronization
release. The system must treat captured pages and text as untrusted input and
must not bypass authentication, paywalls, CAPTCHAs, robots restrictions, or
other access controls.

## Scope refinement

### MVP: local-first usable release

The MVP includes:

- Manifest V3 Chrome/Edge capture with minimum justified permissions.
- Current-page metadata/text extraction where available, selected-text capture,
  and manual paste fallback.
- Preview/edit before save, safe text rendering, duplicate warning, and local
  IndexedDB storage.
- Collections and captured-job management in a local dashboard.
- Versioned Thai/English ontology with aliases and preserved distinctions
  between related technologies.
- Deterministic classification for skills, experience, education, language,
  soft skills, work arrangement, and required/preferred signals.
- Unique-per-job frequencies, confidence, evidence snippets, source-job links,
  and manual corrections.
- Filtering, comparison, CSV/JSON export, accessibility, and responsive
  behavior.
- A governed bilingual corpus and measurable accuracy evaluation method.
- Security tests for hostile text, unsafe URLs, message validation, injection
  boundaries, and permission assumptions.

The MVP must not require cloud accounts, server-side URL fetching, external
AI, file uploads, telemetry, automated crawling, or PDF export.

### Later releases

- WP-06: optional cloud synchronization with authentication, object
  authorization, PostgreSQL, deletion, and conflict handling.
- WP-07: opt-in provider-neutral AI assistance behind schema validation,
  evidence checks, cost controls, and deterministic fallback.
- WP-08: operational hardening, SBOM/scanning, incident response,
  backup/recovery, and release automation.
- WP-09: representative real-world validation, cross-browser verification,
  store preparation, performance testing, and final release review.
- PDF export, additional site adapters, and document upload only after
  separate security and privacy approval.

### Explicit exclusions

Mass crawling, access-control circumvention, automatic applications,
credential/private-message collection, unsupported perfect-accuracy claims,
antivirus functionality, salary prediction, recruitment workflows, native
mobile applications, and premature microservices are out of scope.

## Decisions still requiring confirmation

These are open design decisions, not reasons to expand WP-01:

1. Frontend language, build, package, and test tooling.
2. Supported Java 21 and Spring Boot 3.x lines for the optional backend.
3. Extension page versus separately served local dashboard packaging.
4. Canonical local data model and IndexedDB migration strategy.
5. Ontology coverage, alias governance, and bilingual annotation protocol.
6. Accuracy targets and release thresholds after baseline measurement.
7. Export-only MVP schema and whether a separately approved import/interchange
   is needed before optional synchronization.
8. Cloud authentication and session model.
9. Accessibility conformance target and browser/assistive-technology matrix.
10. Canonical product/repository naming and documentation conventions.

The evidence required for these decisions is recorded in the ADR set under
docs/adr/. No option is accepted by this master plan.

## Work-package dependency map

~~~mermaid
flowchart TD
  WP01[WP-01 scope and governance] --> WP02[WP-02 architecture and security]
  WP02 --> WP03[WP-03 extension capture]
  WP02 --> WP04[WP-04 analysis and ontology]
  WP03 --> WP05[WP-05 local dashboard and reports]
  WP04 --> WP05
  WP05 --> WP08[WP-08 hardening and operations]
  WP08 --> WP09[WP-09 release validation]
  WP02 -. optional later .-> WP06[WP-06 optional backend and sync]
  WP04 -. optional later .-> WP06
  WP06 -. optional later .-> WP07[WP-07 optional AI]
  WP07 -. optional hardening input .-> WP08
~~~

WP-03 and WP-04 may proceed in parallel only after WP-02 freezes their
shared contracts. The local MVP critical path is WP-01 -> WP-02 ->
WP-03/WP-04 -> WP-05 -> WP-08 -> WP-09. WP-06 and WP-07 are optional later
branches; their controls may feed WP-08 and WP-09 when those packages are
approved, but neither gates local MVP hardening or validation.

## Source-of-truth documentation

- [Approved WP-01 plan](wp-01-plan.md)
- [Product brief](../product/product-brief.md)
- [Requirements](../product/requirements.md)
- [Traceability matrix](../product/traceability.md)
- [Glossary](../product/glossary.md)
- [Work-package roadmap](../roadmap/work-packages.md)
- [Engineering governance](../governance/engineering-governance.md)
- [Risk register](../risks/risk-register.md)
- [ADR index](../adr/README.md)
- [Security and privacy baseline](../security/security-privacy-baseline.md)
- [Quality plans](../quality/test-strategy.md)
- [WP-01 acceptance and corrective review handoff](../handoffs/wp-01-acceptance.md)
- [WP-02 planning handoff](../handoffs/wp-02-planning-handoff.md)

Subsequent work packages must update these sources rather than create
parallel sources of truth.

## Governance baseline

Every work package has separate planning, implementation, and review
sessions. Planning produces an approved handoff and stops before
implementation. Implementation changes only the approved package, records
deviations, updates documentation and risks, and hands off to review. Review
is initially independent, reports severity-classified findings with evidence,
and does not silently fix defects.

A package is complete only when acceptance criteria, applicable tests,
security verification, documentation, ADR/risk updates, and handoff are
complete, with no unresolved Critical or High review findings.

## Immediate next step

The WP-01 corrective implementation is recorded in the acceptance report and
is ready for independent review. WP-02 planning may use the WP-02 handoff,
but WP-02 implementation remains blocked until the corrective review closes
and named decision owners are assigned.
