# WP-02 Planning Handoff

Status: Ready for independent re-review and subsequent WP-02 planning; implementation not authorized
Date: 2026-09-17
Source: WP-01 documentation baseline, authorized second corrective amendment,
and acceptance/review handoff
Gate: Independent re-review of the corrective change set remains required before WP-01 is finally accepted

## Handoff purpose

WP-02 should turn the approved local-first product boundary into an
evidence-backed architecture and security foundation. This handoff is a
planning input, not permission to implement code, install dependencies, or
create infrastructure. The local-MVP critical path excludes WP-06 and WP-07;
they remain optional later branches whose controls may feed WP-08/WP-09 only
after separate approval.

## Approved inputs

- Product boundary, personas, journeys, assumptions, and constraints:
  docs/product/product-brief.md
- Stable requirement catalog:
  docs/product/requirements.md
- Requirement-to-package/evidence crosswalk:
  docs/product/traceability.md
- Domain terms and data-separation rules:
  docs/product/glossary.md
- Package dependencies and gates:
  docs/roadmap/work-packages.md
- Session protocol, state vocabulary, Ready/Done, and change control:
  docs/governance/engineering-governance.md
- Review severity and closure rules:
  docs/governance/review-guide.md
- Scoring method and seeded risks:
  docs/risks/method.md and docs/risks/risk-register.md
- Proposed decision records:
  docs/adr/README.md and ADR-0001 through ADR-0010
- Approved plan and corrective review evidence:
  docs/plans/wp-01-plan.md and docs/handoffs/wp-01-acceptance.md
- Preliminary data inventory and trust-boundary questions:
  docs/security/security-privacy-baseline.md
- Accessibility, accuracy, and test planning:
  docs/quality/accessibility-plan.md,
  docs/quality/accuracy-evaluation-plan.md, and
  docs/quality/test-strategy.md

## WP-02 work to plan

1. Confirm product/project/security/privacy/architecture/evaluation/
   accessibility owners and named reviewers.
2. Produce architecture and trust-boundary diagrams covering page capture,
   extension contexts, local store, dashboard, export, and explicitly
   deferred sync/AI paths. Import/interchange behavior and invalid-import
   testing are not MVP inputs unless separately approved.
3. Run a time-boxed frontend/tooling compatibility spike and update
   ADR-0001 with official support, MV3/browser, reproducibility,
   license/security, and update evidence.
4. Decide or time-box local dashboard packaging in ADR-0002.
5. Define the local data contract, stable IDs, and the exact immutable job-text
   value accepted when the job is saved in ADR-0003. Evidence uses
   zero-based, end-exclusive UTF-8 byte offsets and the SHA-256 source digest;
   later metadata edits are not analysis input. Also define migrations,
   recovery, quotas, and export compatibility.
6. Define extension permission, host-access, message, URL, rendering, size,
   and network-observation checks for SEC-001 through SEC-010.
7. Recommend the accessibility target and browser/assistive-technology matrix
   in ADR-0009 before UI implementation.
8. Review corpus/ontology boundary decisions that affect architecture without
   setting accuracy targets prematurely.
9. Update requirements, traceability, risks, and handoff evidence with
   accepted or still-Proposed decisions.

## Unresolved decisions

| Decision | ADR | Required before |
|---|---|---|
| Frontend workspace and tooling | ADR-0001 | WP-02 implementation-ready gate |
| Dashboard packaging | ADR-0002 | WP-03/WP-05 contracts |
| Local data model and migrations | ADR-0003 | WP-03/WP-05 persistence |
| Bilingual ontology governance | ADR-0004 | WP-04 implementation |
| Corpus and accuracy gates | ADR-0005 | WP-04 evaluation |
| Pre-sync interchange | ADR-0006 | WP-05 export; import only if separately approved, then WP-06 planning |
| Backend runtime versions | ADR-0007 | WP-06 only; never MVP |
| Cloud authentication | ADR-0008 | WP-06 only; never MVP |
| Accessibility target/matrix | ADR-0009 | WP-05 UI implementation |
| Naming/documentation conventions | ADR-0010 | Before external tooling/rename |

## Risk gates

WP-02 must review these before implementation starts:

- R-001: untrusted content, message, URL, and rendering boundaries.
- R-002: permission and host-access budget.
- R-003: local data inventory, deletion, and future transmission.
- R-006: migration, recovery, and evidence/correction invariants.
- R-009: repository ownership, review, and recovery policy.
- R-010: accessibility target and manual verification capacity.
- R-013: supported tooling and dependency/update evidence.
- R-014: local MVP remains independent of cloud, AI, backend, and network.

R-004/R-005 become implementation gates for WP-04. R-007/R-008 remain
deferred gates for WP-06/WP-07 and must not enter the local MVP critical path.
WP-08 and WP-09 must still complete local-MVP hardening and validation
without waiting for those optional branches.

## Stop/go conditions

### Stop

Stop WP-02 implementation if:

- An owner or approver for a material security/privacy/accessibility decision
  is unavailable.
- A proposed tool or package lacks support, reproducibility, license, or
  security evidence.
- The architecture requires an account, network, backend URL fetch, or AI for
  the local MVP.
- Original evidence, derived data, corrections, deletion, or migration
  semantics cannot be represented separately.
- A Critical or High risk lacks an owner, treatment, contingency, and
  verification method.
- Independent WP-01 review finds a material scope, link, ID, or status defect
  that would invalidate the handoff.

### Go to implementation planning

Proceed when the stop conditions are cleared, WP-02 decisions have evidence
and authorized status, contracts are versioned, package gates are mapped, and
the WP-02 Definition of Ready is met.

## Expected WP-02 outputs

- Architecture overview and trust-boundary/data-flow diagrams.
- Accepted or still-Proposed ADR updates with related-ADR and evidence links.
- Extension/dashboard packaging recommendation.
- Local data contract, immutable saved-job-text/source-digest/offset contract,
  migration/recovery contract, and export-only boundary.
- Permission, message, URL, rendering, dependency, and network-observation
  verification plan.
- Accessibility target and browser/assistive-technology matrix.
- Updated traceability and risk register.
- WP-03/WP-04/WP-05 implementation-ready contracts and handoff.

## Acceptance expectations

WP-02 must show changed requirements/ADRs/risks, evidence commands and
versions, reviewer/approval roles, unresolved limitations, and a clean
scope boundary. It must not mark a planned control Verified merely because a
design document exists.
