# Architecture Decision Records

Status: Proposed index - no initial decision is accepted
Date: 2026-09-17

Source links: [ADR template](template.md), [Requirements](../product/requirements.md),
[Traceability](../product/traceability.md), [Risk register](../risks/risk-register.md),
[Engineering governance](../governance/engineering-governance.md)

## Lifecycle

ADRs are numbered, immutable decision records under docs/adr/. Status values
are Proposed, Accepted, Rejected, Superseded, and Deprecated. A decision is
Proposed while evidence or authorized approval is incomplete.

Changing an Accepted decision requires a new ADR that supersedes it. The
older record remains readable and its original outcome is not silently
rewritten.

Every ADR includes title/status/date, owners/deciders, context, scope,
options, evidence, decision, consequences, security/privacy/accessibility/
operations effects, validation, rollback or revisit triggers, and related
requirements/risks.

## Index

| ADR | Subject | Status | Evidence required before acceptance | Target package |
|---|---|---|---|---|
| [ADR-0001](0001-frontend-workspace-and-tooling.md) | Frontend workspace, language, build, test, and package tooling | Proposed | Official support, MV3/browser compatibility, reproducible spike, license/security/update review | Proposal in WP-01; accept by WP-02 |
| [ADR-0002](0002-local-dashboard-packaging.md) | Local dashboard packaging | Proposed | Offline journey, permissions/CSP, storage sharing, UX, accessibility/testing, migration | WP-02 |
| [ADR-0003](0003-local-data-model-and-migrations.md) | Local data model, IDs, offsets, storage, and migrations | Proposed | Invariants, browser behavior, migration/backup fixtures, export and performance evidence | WP-02 |
| [ADR-0004](0004-bilingual-ontology-governance.md) | Bilingual ontology, aliases, distinctions, and governance | Proposed | Representative samples, ambiguity review, domain capacity, versioning, provenance | WP-04 |
| [ADR-0005](0005-corpus-and-accuracy-gates.md) | Corpus annotation and accuracy release gates | Proposed | Permitted corpus, annotation trial, baseline slices, uncertainty, user-harm analysis | WP-04 |
| [ADR-0006](0006-pre-sync-interchange.md) | Export-only MVP; separately approved future import/interchange before cloud sync | Proposed | Backup need, privacy/schema risks, round-trip/security prototype, invalid-import testing, support cost | WP-02/WP-05 |
| [ADR-0007](0007-backend-runtime-versions.md) | Optional Java 21 and Spring Boot 3.x runtime line | Proposed | Current official support, compatibility/BOM, advisories, PostgreSQL/deployment evidence | WP-06 |
| [ADR-0008](0008-cloud-authentication.md) | Optional cloud authentication and session model | Proposed | Topology, threat model, identity/privacy, recovery/deletion, authorization prototype | WP-06 |
| [ADR-0009](0009-accessibility-target-and-matrix.md) | Accessibility conformance target and verification matrix | Proposed | Distribution, stakeholder/legal guidance, browsers, assistive technology, review capacity | WP-02 |
| [ADR-0010](0010-naming-and-documentation-conventions.md) | Product/repository naming and documentation conventions | Proposed | Sponsor decision, VCS/hosting constraints, availability, migration cost | WP-01 |

No option in this index is accepted by WP-01.

## Review rules

- Link each decision to requirements and risks.
- Record evidence sources and tool versions where relevant.
- Keep unresolved alternatives visible.
- Do not use Accepted for a recommendation that lacks authorized approval.
- Update the traceability matrix and handoff when a decision changes package
  dependencies or release scope.
