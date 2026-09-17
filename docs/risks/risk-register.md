# Risk Register

Status: Open - corrective WP-01 register; controls remain planned unless
explicitly marked otherwise
Date raised: 2026-09-17
Last reviewed: 2026-09-17
Owner convention: role owners are accountable placeholders until named
individuals are assigned. No individual is invented in this register.

The field structure follows the [risk method](method.md). Residual scores are
not assessed until the stated verification evidence is reviewed.

## Summary

| ID | Title | Inherent score | Severity | Owner role | Status |
|---|---|---:|---|---|---|
| R-001 | Untrusted content crosses an execution or privilege boundary | 4 x 5 = 20 | Critical | Security owner | Open - planned |
| R-002 | Extension permissions exceed justified capture flows | 4 x 4 = 16 | High | Extension lead | Open - planned |
| R-003 | Sensitive job data is transmitted or retained unexpectedly | 3 x 5 = 15 | High | Privacy owner | Open - planned |
| R-004 | Ontology conflates technologies or misses bilingual variants | 4 x 4 = 16 | High | Analysis lead | Open - planned |
| R-005 | Corpus is unrepresentative, impermissible, contaminated, or tuned against | 4 x 4 = 16 | High | Evaluation lead | Open - planned |
| R-006 | Local schema migration corrupts evidence or corrections | 3 x 5 = 15 | High | Architecture owner | Open - planned |
| R-007 | Future cloud authorization exposes another user's captures | 3 x 5 = 15 | High | Backend security owner | Open - deferred |
| R-008 | Optional AI leaks content, fabricates results, or becomes required | 4 x 4 = 16 | High | AI feature owner | Open - deferred |
| R-009 | Git history/review/recovery policy is insufficient for reliable governance | 4 x 4 = 16 | High | Project lead | Open - planned |
| R-010 | Accessibility barriers make core workflows unusable | 3 x 4 = 12 | High | UX/accessibility owner | Open - planned |
| R-011 | Source-site changes make automatic capture unreliable | 4 x 3 = 12 | High | Extension lead | Open - planned |
| R-012 | Export exposes unexpected data or executes spreadsheet formulas | 3 x 4 = 12 | High | Dashboard lead | Open - planned |
| R-013 | Unsupported tooling/browser/backend choices create debt | 3 x 4 = 12 | High | Architecture owner | Open - planned |
| R-014 | Cloud, AI, or backend becomes a hidden MVP dependency | 4 x 3 = 12 | High | Product owner | Open - planned |

## Detailed entries

### R-001 - Untrusted content crosses an execution or privilege boundary

| Field | Value |
|---|---|
| ID | R-001 |
| Title | Untrusted content crosses an execution or privilege boundary |
| Category | Security / input handling |
| Cause | Page text, pasted text, URLs, exports, or future model output is treated as trusted markup or instructions |
| Event | A renderer, parser, or message handler accepts active content or a privileged action |
| Consequence | Script execution, message confusion, data exposure, or privilege misuse |
| Affected requirements/assets | SEC-001, SEC-002, SEC-004, SEC-005; page text, extension contexts, local data |
| Owner role/name | Security owner / named individual unassigned |
| Raised/reviewed | 2026-09-17 / 2026-09-17 |
| Inherent likelihood | 4 |
| Inherent impact | 5 |
| Inherent score/severity | 20 / Critical |
| Current controls/state | Threat model, safe rendering, URL/message schemas / planned |
| Treatment | Freeze trust boundaries and adversarial fixtures before WP-03 implementation |
| Action owner/due point | Security owner with WP-02 / before WP-03 implementation |
| Trigger/early indicator | Raw HTML rendering, dynamic code path, permissive handler, or dangerous URL accepted |
| Contingency | Block release, disable the affected path, remove active content, and investigate |
| Verification method/evidence link | Threat-model review, safe rendering tests, URL/message negative fixtures, independent security review / no evidence yet |
| Residual likelihood/impact/score | Not assessed / Not assessed / Not assessed |
| Status | Open - planned |
| Accepting authority | Security owner and product owner |
| Related ADR/package | [ADR-0002](../adr/0002-local-dashboard-packaging.md), [ADR-0003](../adr/0003-local-data-model-and-migrations.md), [ADR-0006](../adr/0006-pre-sync-interchange.md); WP-02/WP-03/WP-05/WP-07 |

### R-002 - Permissions exceed justified flows

| Field | Value |
|---|---|
| ID | R-002 |
| Title | Extension permissions exceed justified flows |
| Category | Security / privacy / distribution |
| Cause | A permission, host wildcard, or background access is added without a journey-based need |
| Event | The extension requests broader access than capture requires |
| Consequence | Excess browsing-data exposure, trust loss, or distribution rejection |
| Affected requirements/assets | SEC-003, PRIV-001; extension permissions, host access, user trust |
| Owner role/name | Extension lead / named individual unassigned |
| Raised/reviewed | 2026-09-17 / 2026-09-17 |
| Inherent likelihood | 4 |
| Inherent impact | 4 |
| Inherent score/severity | 16 / High |
| Current controls/state | Journey-based permission budget and manifest review / planned |
| Treatment | Map every permission to a capture journey before WP-03 implementation |
| Action owner/due point | Extension lead with architecture owner / before WP-03 implementation |
| Trigger/early indicator | New permission or host wildcard appears in design |
| Contingency | Reject the increase; use active-tab, selection, or paste and defer the adapter |
| Verification method/evidence link | Permission matrix, manifest assertion, browser review, threat-model sign-off / no evidence yet |
| Residual likelihood/impact/score | Not assessed / Not assessed / Not assessed |
| Status | Open - planned |
| Accepting authority | Security owner and product owner |
| Related ADR/package | [ADR-0001](../adr/0001-frontend-workspace-and-tooling.md), [ADR-0002](../adr/0002-local-dashboard-packaging.md); WP-02/WP-03 |

### R-003 - Sensitive data is transmitted or retained unexpectedly

| Field | Value |
|---|---|
| ID | R-003 |
| Title | Sensitive job data is transmitted or retained unexpectedly |
| Category | Privacy / data governance |
| Cause | Telemetry, sync, AI, unclear retention, or corpus capture creates an unreviewed path |
| Event | Captured text, URLs, personal details, derived data, or corrections leave the documented local boundary |
| Consequence | Unexpected privacy exposure or inability to honor deletion expectations |
| Affected requirements/assets | PRIV-001 through PRIV-007, SEC-009; job text, URLs, derived data, corrections, corpus |
| Owner role/name | Privacy owner / named individual unassigned |
| Raised/reviewed | 2026-09-17 / 2026-09-17 |
| Inherent likelihood | 3 |
| Inherent impact | 5 |
| Inherent score/severity | 15 / High |
| Current controls/state | Local-only default, data inventory, purpose-specific consent / planned |
| Treatment | Complete data-flow review and deletion design before any transmission proposal |
| Action owner/due point | Privacy owner with WP-02 / before sync or AI planning |
| Trigger/early indicator | Network dependency, sync/AI proposal, unclear deletion, or corpus without provenance |
| Contingency | Disable transmission, provide deletion/export guidance, and escalate suspected incidents |
| Verification method/evidence link | Data inventory, trust-boundary review, network observation, consent design, deletion tests / no evidence yet |
| Residual likelihood/impact/score | Not assessed / Not assessed / Not assessed |
| Status | Open - planned |
| Accepting authority | Privacy owner and product owner |
| Related ADR/package | [ADR-0002](../adr/0002-local-dashboard-packaging.md), [ADR-0006](../adr/0006-pre-sync-interchange.md), [ADR-0008](../adr/0008-cloud-authentication.md); WP-02/WP-05/WP-06/WP-07 |

### R-004 - Ontology conflates or misses terms

| Field | Value |
|---|---|
| ID | R-004 |
| Title | Ontology conflates technologies or misses bilingual variants |
| Category | Accuracy / domain governance |
| Cause | Aliases, language variants, or related technologies are mapped without context or distinction rules |
| Event | A Thai/English mention receives an unsafe canonical mapping or is omitted |
| Consequence | Misleading comparisons, frequency errors, and user harm |
| Affected requirements/assets | FR-007, FR-009, ACC-001 through ACC-008; ontology, analyzer, evidence |
| Owner role/name | Analysis lead / named individual unassigned |
| Raised/reviewed | 2026-09-17 / 2026-09-17 |
| Inherent likelihood | 4 |
| Inherent impact | 4 |
| Inherent score/severity | 16 / High |
| Current controls/state | Versioned IDs, aliases, distinctions, bilingual corpus / planned |
| Treatment | Run ambiguity/error analysis and review distinction fixtures before baseline targets |
| Action owner/due point | Analysis lead with evaluation lead / before WP-04 baseline |
| Trigger/early indicator | Confusion-pair errors, repeated user remaps, or poor language-slice results |
| Contingency | Label uncertainty, permit remapping, roll back ontology, and narrow claims |
| Verification method/evidence link | Sliced precision/recall/F1, confusion analysis, corpus review, ontology change review / no evidence yet |
| Residual likelihood/impact/score | Not assessed / Not assessed / Not assessed |
| Status | Open - planned |
| Accepting authority | Analysis owner and product owner |
| Related ADR/package | [ADR-0004](../adr/0004-bilingual-ontology-governance.md), [ADR-0005](../adr/0005-corpus-and-accuracy-gates.md); WP-04 |

### R-005 - Corpus invalidates accuracy claims

| Field | Value |
|---|---|
| ID | R-005 |
| Title | Corpus is unrepresentative, impermissible, contaminated, or tuned against |
| Category | Accuracy / privacy / evaluation governance |
| Cause | Samples have unknown permission, skew, leakage, duplication, or direct tuning against hidden evaluation data |
| Event | Metrics are calculated from an invalid or undisclosed corpus |
| Consequence | Invalid accuracy claims, improper retention, or unsafe release decisions |
| Affected requirements/assets | PRIV-006, ACC-001 through ACC-007; corpus, annotation, evaluation artifacts |
| Owner role/name | Evaluation lead / named individual unassigned |
| Raised/reviewed | 2026-09-17 / 2026-09-17 |
| Inherent likelihood | 4 |
| Inherent impact | 4 |
| Inherent score/severity | 16 / High |
| Current controls/state | Corpus register, minimization, fixed splits, double annotation, provenance review / planned |
| Treatment | Freeze corpus policy and annotation guide before evaluation implementation |
| Action owner/due point | Evaluation lead with privacy owner / before WP-04 evaluation |
| Trigger/early indicator | Unknown provenance, skewed slices, duplicate leakage, or target before baseline |
| Contingency | Withdraw claims/artifacts, rebuild corpus, and repeat independent evaluation |
| Verification method/evidence link | Permission/minimization review, split/leakage check, agreement record, baseline report / no evidence yet |
| Residual likelihood/impact/score | Not assessed / Not assessed / Not assessed |
| Status | Open - planned |
| Accepting authority | Evaluation owner and privacy owner |
| Related ADR/package | [ADR-0004](../adr/0004-bilingual-ontology-governance.md), [ADR-0005](../adr/0005-corpus-and-accuracy-gates.md); WP-04 |

### R-006 - Schema migration corrupts evidence

| Field | Value |
|---|---|
| ID | R-006 |
| Title | Local schema migration corrupts evidence or corrections |
| Category | Data integrity / recovery |
| Cause | An IndexedDB schema change lacks fixtures, rollback, or interrupted-upgrade handling |
| Event | Migration loses or orphans links between evidence, analysis, corrections, or exports |
| Consequence | Data loss, unrecoverable evidence, or misleading results |
| Affected requirements/assets | FR-004, FR-013, NFR-003, NFR-005; local store, evidence, corrections, exports |
| Owner role/name | Architecture owner / named individual unassigned |
| Raised/reviewed | 2026-09-17 / 2026-09-17 |
| Inherent likelihood | 3 |
| Inherent impact | 5 |
| Inherent score/severity | 15 / High |
| Current controls/state | Versioned schema ADR, invariants, migration fixtures, export/recovery path / planned |
| Treatment | Define transaction, UTF-8 span, and recovery contracts before persistence implementation |
| Action owner/due point | Architecture owner with dashboard lead / before WP-05 persistence |
| Trigger/early indicator | Missing migration fixture or interrupted upgrade loses links |
| Contingency | Stop upgrade, preserve old store, restore compatible export, ship corrective migration |
| Verification method/evidence link | Migration matrix, fault injection, invariants, quota/transaction evidence, span-digest fixtures / no evidence yet |
| Residual likelihood/impact/score | Not assessed / Not assessed / Not assessed |
| Status | Open - planned |
| Accepting authority | Architecture owner |
| Related ADR/package | [ADR-0003](../adr/0003-local-data-model-and-migrations.md), [ADR-0006](../adr/0006-pre-sync-interchange.md); WP-02/WP-05 |

### R-007 - Cloud authorization exposes another user

| Field | Value |
|---|---|
| ID | R-007 |
| Title | Future cloud authorization exposes another user's captures |
| Category | Cloud security / authorization |
| Cause | A future API trusts a user-controlled object ID without an independent object-authorization check |
| Event | A user reads or mutates another user's capture through sync |
| Consequence | Cross-user disclosure or mutation |
| Affected requirements/assets | FR-014, SEC-008, NFR-007; future cloud captures, identity, sessions |
| Owner role/name | Backend security owner / named individual unassigned |
| Raised/reviewed | 2026-09-17 / 2026-09-17 |
| Inherent likelihood | 3 |
| Inherent impact | 5 |
| Inherent score/severity | 15 / High |
| Current controls/state | Deferred authorization requirement and negative-test plan / planned |
| Treatment | Create tenancy/threat model and authorization contract before WP-06 implementation |
| Action owner/due point | Backend security owner / before WP-06 implementation |
| Trigger/early indicator | Sync endpoint lacks a negative object-policy test |
| Contingency | Block sync release, disable endpoint, revoke affected tokens, invoke incident response |
| Verification method/evidence link | Multi-user negative integration tests, code review, threat model, operational exercise / no evidence yet |
| Residual likelihood/impact/score | Not assessed / Not assessed / Not assessed |
| Status | Open - deferred |
| Accepting authority | Security owner |
| Related ADR/package | [ADR-0007](../adr/0007-backend-runtime-versions.md), [ADR-0008](../adr/0008-cloud-authentication.md); WP-06 |

### R-008 - Optional AI becomes unsafe or required

| Field | Value |
|---|---|
| ID | R-008 |
| Title | Optional AI leaks content, fabricates results, or becomes required |
| Category | AI security / privacy / scope |
| Cause | Captured content is sent without granular consent, output lacks evidence, or fallback is unusable |
| Event | AI becomes a hidden dependency or returns unsupported qualifications |
| Consequence | Privacy exposure, fabricated signals, or loss of local-MVP independence |
| Affected requirements/assets | FR-015, SEC-006, PRIV-003, ACC-008; captured text, provider boundary, deterministic analyzer |
| Owner role/name | AI feature owner / named individual unassigned |
| Raised/reviewed | 2026-09-17 / 2026-09-17 |
| Inherent likelihood | 4 |
| Inherent impact | 4 |
| Inherent score/severity | 16 / High |
| Current controls/state | Default-off, schema/evidence validation, quotas, deterministic fallback / planned and deferred |
| Treatment | Validate consent, provider disclosure, evidence checks, and outage fallback before WP-07 |
| Action owner/due point | AI feature owner with privacy owner / before WP-07 implementation |
| Trigger/early indicator | Content transmitted without purpose consent, result lacks evidence, or fallback fails |
| Contingency | Disable provider, discard unverified outputs, retain/recompute deterministic results |
| Verification method/evidence link | Consent/network tests, schema/evidence validation, budgets, provider-unavailable journey / no evidence yet |
| Residual likelihood/impact/score | Not assessed / Not assessed / Not assessed |
| Status | Open - deferred |
| Accepting authority | Privacy owner and product owner |
| Related ADR/package | [ADR-0005](../adr/0005-corpus-and-accuracy-gates.md), [ADR-0008](../adr/0008-cloud-authentication.md); WP-07 |

### R-009 - Governance depends on insufficient source control

| Field | Value |
|---|---|
| ID | R-009 |
| Title | Git history, review, or recovery policy is insufficient |
| Category | Delivery / governance / recoverability |
| Cause | Git metadata exists but ownership, review, remote recovery, branch, or backup policy is not established |
| Event | A material change is lost, unreviewed, or unrecoverable |
| Consequence | Lost decisions, weak auditability, or inability to restore the baseline |
| Affected requirements/assets | NFR-006, SEC-010; repository history, documentation, future source |
| Owner role/name | Project lead / named individual unassigned |
| Raised/reviewed | 2026-09-17 / 2026-09-17 |
| Inherent likelihood | 4 |
| Inherent impact | 4 |
| Inherent score/severity | 16 / High |
| Current controls/state | Git repository, branch, and history observed; review/recovery policy / partly observed, policy planned |
| Treatment | Confirm repository ownership, review convention, backup/recovery, and remote policy before code |
| Action owner/due point | Project lead / before application implementation |
| Trigger/early indicator | No recoverable remote/backup, uncontrolled direct changes, or missing review record |
| Contingency | Pause implementation, archive docs, and establish a reviewed baseline |
| Verification method/evidence link | Ownership record, branch/review check, recovery exercise, acceptance review / no evidence yet |
| Residual likelihood/impact/score | Not assessed / Not assessed / Not assessed |
| Status | Open - planned |
| Accepting authority | Project lead |
| Related ADR/package | [ADR-0010](../adr/0010-naming-and-documentation-conventions.md); all packages |

### R-010 - Accessibility barriers block core use

| Field | Value |
|---|---|
| ID | R-010 |
| Title | Accessibility barriers make core workflows unusable |
| Category | Accessibility / user experience |
| Cause | Keyboard traps, inaccessible statuses/evidence, contrast, zoom, reflow, or screen-reader failures remain undiscovered |
| Event | A user cannot complete capture, evidence review, correction, export, or deletion |
| Consequence | Core workflows are unavailable and release acceptance fails |
| Affected requirements/assets | A11Y-001 through A11Y-006; capture, fallback, evidence, comparison, export, deletion |
| Owner role/name | UX/accessibility owner / named individual unassigned |
| Raised/reviewed | 2026-09-17 / 2026-09-17 |
| Inherent likelihood | 3 |
| Inherent impact | 4 |
| Inherent score/severity | 12 / High |
| Current controls/state | Target-setting ADR and automated/manual matrix / planned |
| Treatment | Select target and representative matrix before UI implementation |
| Action owner/due point | UX/accessibility owner / during WP-02 planning |
| Trigger/early indicator | Keyboard trap, inaccessible evidence, contrast/reflow failure, or missing AT evidence |
| Contingency | Block affected workflow release and remediate or provide accessible alternative |
| Verification method/evidence link | Automated checks, keyboard/focus/zoom/reflow/screen-reader review, independent review / no evidence yet |
| Residual likelihood/impact/score | Not assessed / Not assessed / Not assessed |
| Status | Open - planned |
| Accepting authority | Accessibility owner and product owner |
| Related ADR/package | [ADR-0009](../adr/0009-accessibility-target-and-matrix.md); WP-02/WP-05/WP-09 |

### R-011 - Source sites change or block extraction

| Field | Value |
|---|---|
| ID | R-011 |
| Title | Source-site changes make automatic capture unreliable |
| Category | Product reliability / extension |
| Cause | Page structure, access behavior, or content format changes |
| Event | Automatic extraction is empty, incomplete, or misleading |
| Consequence | Capture reliability falls while users still need a safe fallback |
| Affected requirements/assets | FR-002, FR-003, SEC-003, NFR-005; page extraction, selection, manual paste |
| Owner role/name | Extension lead / named individual unassigned |
| Raised/reviewed | 2026-09-17 / 2026-09-17 |
| Inherent likelihood | 4 |
| Inherent impact | 3 |
| Inherent score/severity | 12 / High |
| Current controls/state | Generic extraction contract, fixtures, preview/edit, selection/paste fallback / planned |
| Treatment | Define adapter limitations and manual-fallback acceptance before WP-03 release |
| Action owner/due point | Extension lead / before WP-03 release |
| Trigger/early indicator | Extraction regression or approved success-threshold breach |
| Contingency | Disable broken adapter, preserve manual capture, document limitation |
| Verification method/evidence link | Fixture regression, representative manual scenarios, fallback end-to-end evidence / no evidence yet |
| Residual likelihood/impact/score | Not assessed / Not assessed / Not assessed |
| Status | Open - planned |
| Accepting authority | Extension lead and product owner |
| Related ADR/package | [ADR-0001](../adr/0001-frontend-workspace-and-tooling.md), [ADR-0002](../adr/0002-local-dashboard-packaging.md); WP-03/WP-05 |

### R-012 - Export leaks or executes content

| Field | Value |
|---|---|
| ID | R-012 |
| Title | Export exposes unexpected data or executes spreadsheet formulas |
| Category | Export security / privacy |
| Cause | Export includes unreviewed fields or CSV cells begin with formula markers |
| Event | A user opens a crafted export in a spreadsheet application |
| Consequence | Privacy disclosure or formula-driven code/data action |
| Affected requirements/assets | FR-012, SEC-006, PRIV-004; JSON/CSV exports, captured text, derived data |
| Owner role/name | Dashboard lead / named individual unassigned |
| Raised/reviewed | 2026-09-17 / 2026-09-17 |
| Inherent likelihood | 3 |
| Inherent impact | 4 |
| Inherent score/severity | 12 / High |
| Current controls/state | Data classification, explicit export schema/preview, neutralization, round-trip tests / planned |
| Treatment | Freeze export-only schema and escaping rules before WP-05 release |
| Action owner/due point | Dashboard lead with security owner / before WP-05 release |
| Trigger/early indicator | Exported fields exceed reviewed schema or formula markers execute |
| Contingency | Disable affected format, advise deletion/re-export, patch encoder |
| Verification method/evidence link | Schema snapshot, malicious-cell fixtures, round-trip tests, security review / no evidence yet |
| Residual likelihood/impact/score | Not assessed / Not assessed / Not assessed |
| Status | Open - planned |
| Accepting authority | Security owner and product owner |
| Related ADR/package | [ADR-0006](../adr/0006-pre-sync-interchange.md); WP-05 |

### R-013 - Unsupported technical choices create debt

| Field | Value |
|---|---|
| ID | R-013 |
| Title | Unsupported tooling, browser, or backend choices create debt |
| Category | Architecture / supply chain / compatibility |
| Cause | A choice lacks official support, compatibility, license, security, or update evidence |
| Event | Selected tooling fails target behavior or becomes costly/unsafe to maintain |
| Consequence | Rework, vulnerabilities, incompatible release, or hidden dependency |
| Affected requirements/assets | NFR-006, SEC-010; frontend tooling, browser targets, optional backend |
| Owner role/name | Architecture owner / named individual unassigned |
| Raised/reviewed | 2026-09-17 / 2026-09-17 |
| Inherent likelihood | 3 |
| Inherent impact | 4 |
| Inherent score/severity | 12 / High |
| Current controls/state | Time-boxed spike, official-source evidence, ADR review / planned |
| Treatment | Complete support/license/security review before accepting ADR-0001 or ADR-0007 |
| Action owner/due point | Architecture owner / before the affected package starts implementation |
| Trigger/early indicator | Choice lacks support horizon, compatibility proof, or update policy |
| Contingency | Replace before implementation expands and isolate stable contracts |
| Verification method/evidence link | Support matrix, reproducible spike, dependency/license review, accepted ADR / no evidence yet |
| Residual likelihood/impact/score | Not assessed / Not assessed / Not assessed |
| Status | Open - planned |
| Accepting authority | Architecture owner |
| Related ADR/package | [ADR-0001](../adr/0001-frontend-workspace-and-tooling.md), [ADR-0007](../adr/0007-backend-runtime-versions.md); WP-02/WP-06/WP-08 |

### R-014 - Scope drift creates an MVP dependency

| Field | Value |
|---|---|
| ID | R-014 |
| Title | Cloud, AI, or backend becomes a hidden MVP dependency |
| Category | Product scope / privacy / delivery |
| Cause | MVP acceptance begins requiring an account, server, AI, import, or network |
| Event | Optional later capability enters the local critical path without reapproval |
| Consequence | Increased scope, privacy/security burden, delayed value, invalid acceptance |
| Affected requirements/assets | NFR-001, SEC-009, PRIV-001, FR-014, FR-015; local MVP path and acceptance |
| Owner role/name | Product owner / named individual unassigned |
| Raised/reviewed | 2026-09-17 / 2026-09-17 |
| Inherent likelihood | 4 |
| Inherent impact | 3 |
| Inherent score/severity | 12 / High |
| Current controls/state | Requirement traceability, explicit roadmap gates, local offline acceptance / planned |
| Treatment | Review every change; keep WP-06/WP-07 optional and import deferred unless separately approved |
| Action owner/due point | Product owner / each package gate |
| Trigger/early indicator | MVP criterion references account, server, AI, import, or network |
| Contingency | Remove dependency or move it later and reapprove the value case |
| Verification method/evidence link | Scope review, offline acceptance scenario, dependency-graph review, change record / no evidence yet |
| Residual likelihood/impact/score | Not assessed / Not assessed / Not assessed |
| Status | Open - planned |
| Accepting authority | Product owner |
| Related ADR/package | [ADR-0006](../adr/0006-pre-sync-interchange.md), [ADR-0007](../adr/0007-backend-runtime-versions.md), [ADR-0008](../adr/0008-cloud-authentication.md); all packages |

## Current follow-up

Assign individual owners before any package requiring their approval is
marked Ready. WP-02 must review all High/Critical entries before architecture
implementation begins. A role assignment is not a named-person assignment,
and no residual score is reduced by documentation alone.
