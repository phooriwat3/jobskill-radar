# Requirement Traceability

Status: Draft - WP-01 source of truth
Date: 2026-09-17
Purpose: map every stable requirement to its responsible package, planned
evidence, and WP-01 acceptance coverage.

The WP-01 acceptance IDs refer to the approved plan's criteria. A mapping to
an acceptance criterion means the documentation baseline covers the
requirement; it does not mean the product behavior is implemented or tested.

| Requirement | Responsible package | Planned evidence | WP-01 coverage |
|---|---|---|---|
| [FR-001](requirements.md#fr-001) | WP-03 | Explicit-action interaction and permission tests | WP01-AC-02, AC-03, AC-11 |
| [FR-002](requirements.md#fr-002) | WP-03 | Page, selection, paste, and extraction fixtures | WP01-AC-02, AC-04 |
| [FR-003](requirements.md#fr-003) | WP-03/WP-05 | Preview/edit end-to-end evidence | WP01-AC-02, AC-04 |
| [FR-004](requirements.md#fr-004) | WP-02/WP-05 | Data contract, persistence, and immutability tests | WP01-AC-03, AC-05, AC-11 |
| [FR-005](requirements.md#fr-005) | WP-05 | Local store CRUD and collection tests | WP01-AC-02, AC-06 |
| [FR-006](requirements.md#fr-006) | WP-05 | Duplicate fixtures and non-blocking warning test | WP01-AC-02 |
| [FR-007](requirements.md#fr-007) | WP-04 | Bilingual corpus evaluation by category and language | WP01-AC-02, AC-10 |
| [FR-008](requirements.md#fr-008) | WP-04/WP-05 | Evidence-link contract and UI inspection tests | WP01-AC-03, AC-05, AC-11 |
| [FR-009](requirements.md#fr-009) | WP-04 | Repeated-mention and alias aggregation fixtures | WP01-AC-05, AC-10 |
| [FR-010](requirements.md#fr-010) | WP-05 | Correction overlay and original-evidence immutability tests | WP01-AC-04, AC-05 |
| [FR-011](requirements.md#fr-011) | WP-05 | Filter and comparison workflow tests | WP01-AC-02 |
| [FR-012](requirements.md#fr-012) | WP-05 | Versioned JSON/CSV schema, escaping, and exported-file round-trip tests | WP01-AC-02, AC-11 |
| [FR-013](requirements.md#fr-013) | WP-05 | Individual, collection, and all-data deletion tests | WP01-AC-04, AC-11 |
| [FR-014](requirements.md#fr-014) | WP-06 | Multi-user authorization, deletion, version, and conflict tests | WP01-AC-06, AC-11 |
| [FR-015](requirements.md#fr-015) | WP-07 | Consent, provider failure, evidence validation, and fallback tests | WP01-AC-06, AC-11 |
| [NFR-001](requirements.md#nfr-001) | WP-03/WP-05 | Offline journey and network-observation evidence | WP01-AC-02, AC-06, AC-11 |
| [NFR-002](requirements.md#nfr-002) | WP-04 | Golden input/output and stable serialization | WP01-AC-03, AC-10 |
| [NFR-003](requirements.md#nfr-003) | WP-02/WP-05 | Migration contract, fixtures, and export compatibility | WP01-AC-03, AC-06 |
| [NFR-004](requirements.md#nfr-004) | WP-02/WP-05 | Approved budgets, volume study, and device/browser baseline | WP01-AC-06 |
| [NFR-005](requirements.md#nfr-005) | WP-02/WP-05 | Fault injection, committed-record preservation, and recovery evidence | WP01-AC-07, AC-11 |
| [NFR-006](requirements.md#nfr-006) | WP-02/WP-08 | Official support, license, security, lockfile, and update review | WP01-AC-09, AC-14 |
| [NFR-007](requirements.md#nfr-007) | WP-06/WP-08 | Service objectives, observability, restore, and incident exercises | WP01-AC-06, AC-07 |
| [SEC-001](requirements.md#sec-001) | WP-02/WP-03 | Hostile text, safe rendering, and execution-boundary tests | WP01-AC-11 |
| [SEC-002](requirements.md#sec-002) | WP-02/WP-03 | Rendering standard, sanitizer boundary decision, and adversarial fixtures | WP01-AC-09, AC-11 |
| [SEC-003](requirements.md#sec-003) | WP-02/WP-03 | Permission budget, manifest review, and capture-flow mapping | WP01-AC-11 |
| [SEC-004](requirements.md#sec-004) | WP-02/WP-03 | Message schema, sender validation, size limits, and negative tests | WP01-AC-11 |
| [SEC-005](requirements.md#sec-005) | WP-03/WP-05 | URL scheme allowlist and dangerous-link tests | WP01-AC-11 |
| [SEC-006](requirements.md#sec-006) | WP-05/WP-07 | Bounded schema validation and safe-failure tests | WP01-AC-09, AC-11 |
| [SEC-007](requirements.md#sec-007) | WP-02/WP-08 | Secret scan and build artifact review | WP01-AC-11, AC-14 |
| [SEC-008](requirements.md#sec-008) | WP-06 | Negative object-authorization tests for every operation | WP01-AC-06, AC-11 |
| [SEC-009](requirements.md#sec-009) | All packages | Architecture boundary and network-observation evidence | WP01-AC-02, AC-06, AC-11 |
| [SEC-010](requirements.md#sec-010) | WP-02/WP-08 | Provenance, vulnerability, update, and reproducible-build review | WP01-AC-09, AC-14 |
| [PRIV-001](requirements.md#priv-001) | WP-02/WP-03/WP-05 | Data-flow review and offline/network tests | WP01-AC-02, AC-11 |
| [PRIV-002](requirements.md#priv-002) | WP-03 | Preview inspection journey | WP01-AC-04, AC-11 |
| [PRIV-003](requirements.md#priv-003) | WP-06/WP-07 | Purpose-specific consent and transmission tests | WP01-AC-06, AC-11 |
| [PRIV-004](requirements.md#priv-004) | WP-05 | Export and deletion evidence including derived data | WP01-AC-04, AC-11 |
| [PRIV-005](requirements.md#priv-005) | All packages | Release data inventory and deletion review | WP01-AC-11 |
| [PRIV-006](requirements.md#priv-006) | WP-04 | Corpus register, permission, minimization, and provenance review | WP01-AC-10, AC-11 |
| [PRIV-007](requirements.md#priv-007) | All packages | Documentation review for behavior versus legal claims | WP01-AC-11, AC-15 |
| [A11Y-001](requirements.md#a11y-001) | WP-05 | Keyboard, focus, and end-to-end workflow matrix | WP01-AC-04, AC-12 |
| [A11Y-002](requirements.md#a11y-002) | WP-02/WP-05 | Automated semantics checks and manual review | WP01-AC-12 |
| [A11Y-003](requirements.md#a11y-003) | WP-02/WP-05 | Approved contrast/target-size criteria and manual checks | WP01-AC-12 |
| [A11Y-004](requirements.md#a11y-004) | WP-05 | Viewport, zoom, and reflow matrix | WP01-AC-04, AC-12 |
| [A11Y-005](requirements.md#a11y-005) | WP-04/WP-05 | Mixed-language, long-token, and reflow fixtures | WP01-AC-04, AC-12 |
| [A11Y-006](requirements.md#a11y-006) | WP-02 | Target ADR and browser/assistive-technology matrix | WP01-AC-12 |
| [ACC-001](requirements.md#acc-001) | WP-04 | Version manifest for ontology, analyzer, corpus, guide, and reports | WP01-AC-03, AC-10 |
| [ACC-002](requirements.md#acc-002) | WP-04 | Per-category/language precision, recall, F1, and support report | WP01-AC-10 |
| [ACC-003](requirements.md#acc-003) | WP-04 | Separate entity, evidence-span, and required/preferred scores | WP01-AC-10 |
| [ACC-004](requirements.md#acc-004) | WP-04 | Frozen matching and canonical-equivalence specification | WP01-AC-05, AC-10 |
| [ACC-005](requirements.md#acc-005) | WP-04 | Split manifest and leakage review | WP01-AC-10 |
| [ACC-006](requirements.md#acc-006) | WP-04 | Baseline report followed by target decision record | WP01-AC-10 |
| [ACC-007](requirements.md#acc-007) | WP-04 | Dataset, slice, exclusion, uncertainty, and limitation report | WP01-AC-10 |
| [ACC-008](requirements.md#acc-008) | All packages | Product/documentation review of accuracy language | WP01-AC-11, AC-15 |

## Acceptance crosswalk

| WP-01 criterion | Primary evidence |
|---|---|
| WP01-AC-01 | Master-plan baseline and WP-01 acceptance repository inspection |
| WP01-AC-02 | Product brief, requirements, roadmap, and scope checks |
| WP01-AC-03 | Requirements catalog and this matrix |
| WP01-AC-04 | Product brief personas and journeys; accessibility plan |
| WP01-AC-05 | Glossary and accuracy plan |
| WP01-AC-06 | Work-package roadmap and ADR index |
| WP01-AC-07 | Engineering governance and review guide |
| WP01-AC-08 | Risk method and risk register |
| WP01-AC-09 | ADR template, index, and ten Proposed ADRs |
| WP01-AC-10 | Accuracy evaluation plan and test strategy |
| WP01-AC-11 | Security/privacy baseline, requirements, and test strategy |
| WP01-AC-12 | Accessibility plan and ADR-0009 |
| WP01-AC-13 | WP-01 acceptance check log |
| WP01-AC-14 | Git file inventory and WP-01 acceptance scope statement |
| WP01-AC-15 | Independent review record; pending until a reviewer is assigned |
