# Risk Register

Status: Open - seeded WP-01 register; controls are planned only  
Date raised: 2026-09-17  
Last review: 2026-09-17  
Owner convention: role owners are accountable placeholders until named
individuals are assigned.

No entry below is marked implemented, tested, or verified solely because it
appears in this register. Residual scores remain unassessed until evidence
exists.

## Summary

| ID | Title | Inherent score | Severity | Owner role | Current status |
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

## Risk details

### R-001 - Untrusted content crosses a boundary

- Cause/event: Page text, pasted text, imports, URLs, or future model output
  is rendered, parsed, or handled as executable or privileged content.
- Consequence/assets: Script execution, message confusion, data exposure, or
  privilege misuse; captured content and extension contexts are affected.
- Requirements/packages: SEC-001, SEC-002, SEC-004, SEC-005; WP-02/WP-03/WP-05/WP-07.
- Owner: Security owner; named person not yet assigned.
- Inherent score: likelihood 4 x impact 5 = 20, Critical.
- Current controls: Threat-model and safe-rendering rules, state planned.
- Treatment/action owner/due: Freeze trust boundaries and adversarial fixtures
  before WP-03 implementation; security owner with WP-02.
- Trigger: Raw HTML rendering, dynamic code path, permissive message handler,
  or dangerous URL accepted.
- Contingency: Block release and disable the affected capture/rendering path;
  remove active content and investigate.
- Verification: Threat-model review, safe text/rendering tests, URL/message
  negative fixtures, and independent security review.
- Residual: Not assessed until evidence; accepting authority is security owner
  and product owner.

### R-002 - Permissions exceed justified flows

- Cause/event: A new extension permission, host wildcard, or background access
  is added without a journey-based need.
- Consequence/assets: Excess browsing-data exposure, user trust loss, or
  distribution/store rejection.
- Requirements/packages: SEC-003, PRIV-001; WP-02/WP-03.
- Owner: Extension lead; named person not yet assigned.
- Inherent score: 4 x 4 = 16, High.
- Current controls: Permission budget and manifest review, state planned.
- Treatment/action owner/due: Map every permission to a capture journey before
  WP-03 implementation; extension lead with architecture owner.
- Trigger: New permission or host wildcard appears in the design.
- Contingency: Reject the increase; use active-tab, selection, or paste flow
  and defer the adapter.
- Verification: Permission matrix, manifest assertion, browser review, and
  threat-model sign-off.
- Residual: Not assessed; accepting authority is security owner and product owner.

### R-003 - Sensitive data is transmitted or retained unexpectedly

- Cause/event: Telemetry, sync, AI, unclear retention, or corpus capture
  creates an unreviewed transmission or storage path.
- Consequence/assets: Privacy loss involving job text, URLs, personal details,
  derived data, or corrections.
- Requirements/packages: PRIV-001 through PRIV-007, SEC-009; all packages.
- Owner: Privacy owner; named person not yet assigned.
- Inherent score: 3 x 5 = 15, High.
- Current controls: Local-only default and data inventory, state planned.
- Treatment/action owner/due: Complete data-flow review and deletion design
  before any transmission proposal; privacy owner with WP-02.
- Trigger: Network dependency, sync/AI proposal, unclear deletion, or corpus
  material without provenance.
- Contingency: Disable transmission, provide deletion/export guidance, and
  escalate any suspected incident for assessment.
- Verification: Data inventory, trust-boundary review, network observation,
  explicit-consent design, and deletion tests.
- Residual: Not assessed; accepting authority is privacy owner and product owner.

### R-004 - Ontology conflates or misses terms

- Cause/event: Aliases, language variants, or related technologies are mapped
  without context and distinction rules.
- Consequence/assets: Misleading comparisons, frequency errors, and user harm
  in Thai/English analysis.
- Requirements/packages: FR-007, FR-009, ACC-001 through ACC-008; WP-04.
- Owner: Analysis lead; named person not yet assigned.
- Inherent score: 4 x 4 = 16, High.
- Current controls: Versioned IDs, aliases, distinctions, and bilingual corpus,
  state planned.
- Treatment/action owner/due: Run ambiguity/error analysis and review
  distinction fixtures before baseline targets; analysis lead with evaluation lead.
- Trigger: Confusion-pair errors, repeated user remaps, or poor language-slice
  results.
- Contingency: Label uncertainty, permit remapping, roll back ontology, and
  narrow supported claims.
- Verification: Sliced precision/recall/F1, confusion analysis, corpus review,
  and ontology change review.
- Residual: Not assessed; accepting authority is analysis and product owner.

### R-005 - Corpus invalidates accuracy claims

- Cause/event: Samples have unknown permission, skew, leakage, duplication,
  or direct tuning against the hidden evaluation set.
- Consequence/assets: Invalid metrics, improper retention, and unsupported
  product claims.
- Requirements/packages: PRIV-006, ACC-001 through ACC-007; WP-04.
- Owner: Evaluation lead; named person not yet assigned.
- Inherent score: 4 x 4 = 16, High.
- Current controls: Corpus register, minimization, fixed splits, double
  annotation, and provenance review, state planned.
- Treatment/action owner/due: Freeze corpus policy and annotation guide before
  evaluation implementation; evaluation lead with privacy owner.
- Trigger: Unknown provenance, skewed slices, duplicate leakage, or target
  selected before baseline.
- Contingency: Withdraw affected claims/artifacts, rebuild the corpus, and
  repeat independent evaluation.
- Verification: Permission/minimization review, split/leakage check,
  agreement/adjudication record, and baseline report.
- Residual: Not assessed; accepting authority is evaluation and privacy owner.

### R-006 - Schema migration corrupts evidence

- Cause/event: An IndexedDB schema change lacks fixtures, rollback, or
  interrupted-upgrade handling.
- Consequence/assets: Lost/orphaned original evidence, analysis, corrections,
  or exports.
- Requirements/packages: FR-004, FR-013, NFR-003, NFR-005; WP-02/WP-05.
- Owner: Architecture owner; named person not yet assigned.
- Inherent score: 3 x 5 = 15, High.
- Current controls: Versioned schema ADR, invariants, migration fixtures, and
  export/restore path, state planned.
- Treatment/action owner/due: Define transaction and recovery contract before
  WP-05 persistence implementation; architecture owner with dashboard lead.
- Trigger: Migration lacks fixture coverage, or interrupted upgrade loses links.
- Contingency: Stop upgrade, preserve old store, restore/import a compatible
  export, and ship a corrective migration.
- Verification: Migration matrix, fault injection, invariant tests, and
  browser quota/transaction evidence.
- Residual: Not assessed; accepting authority is architecture owner.

### R-007 - Cloud authorization exposes another user

- Cause/event: Future API trusts a user-controlled object ID without an
  independent object-authorization check.
- Consequence/assets: Cross-user capture disclosure or mutation.
- Requirements/packages: FR-014, SEC-008, NFR-007; WP-06.
- Owner: Backend security owner; named person not yet assigned.
- Inherent score: 3 x 5 = 15, High.
- Current controls: Deferred authorization requirement and negative-test plan,
  state planned.
- Treatment/action owner/due: Create tenancy/threat model and authorization
  contract before WP-06 implementation; backend security owner.
- Trigger: Any sync endpoint accepts an object ID without a negative policy test.
- Contingency: Block sync release, disable the endpoint, revoke affected
  tokens, and invoke incident response.
- Verification: Multi-user integration tests, code review, threat model, and
  operational exercise.
- Residual: Not assessed; accepting authority is security owner.

### R-008 - Optional AI becomes unsafe or required

- Cause/event: Captured content is sent without granular consent, model output
  lacks evidence, or deterministic fallback is not usable.
- Consequence/assets: Privacy exposure, fabricated qualification signals, or
  cloud dependency in the MVP.
- Requirements/packages: FR-015, SEC-006, PRIV-003, ACC-008; WP-07.
- Owner: AI feature owner; named person not yet assigned.
- Inherent score: 4 x 4 = 16, High.
- Current controls: Default-off, schema/evidence validation, quotas, and
  fallback plan, state planned and deferred.
- Treatment/action owner/due: Validate consent, provider/data disclosure, and
  outage fallback before WP-07 implementation; AI feature owner.
- Trigger: Content transmitted without purpose-specific consent, result lacks
  evidence, or deterministic tests fail without a provider.
- Contingency: Disable provider functionality, discard unverified outputs, and
  retain/recompute deterministic results.
- Verification: Consent/network tests, schema/evidence validation, budget
  tests, and provider-unavailable end-to-end journey.
- Residual: Not assessed; accepting authority is privacy and product owner.

### R-009 - Governance depends on insufficient source control

- Cause/event: Git metadata exists, but review, remote recovery, branch, or
  backup policy is not established or is unavailable.
- Consequence/assets: Lost decisions, unreviewable changes, or inability to
  recover the documentation baseline.
- Requirements/packages: NFR-006, SEC-010; all packages.
- Owner: Project lead; named person not yet assigned.
- Inherent score: 4 x 4 = 16, High.
- Current controls: Git repository and current branch/history observed; review
  and recoverability policy remains planned.
- Treatment/action owner/due: Confirm repository ownership, review convention,
  backup/recovery, and remote policy before code begins; project lead.
- Trigger: No recoverable remote/backup, uncontrolled direct changes, or
  missing review record.
- Contingency: Pause implementation, archive the docs safely, and establish a
  reviewed baseline before code.
- Verification: Repository ownership record, branch/review check, recovery
  exercise, and acceptance review.
- Residual: Not assessed; accepting authority is project lead.

### R-010 - Accessibility barriers block core use

- Cause/event: Keyboard traps, inaccessible status/evidence states, contrast,
  zoom, reflow, or screen-reader failures remain undiscovered.
- Consequence/assets: Core workflows unavailable to users and release risk.
- Requirements/packages: A11Y-001 through A11Y-006; WP-02/WP-05/WP-09.
- Owner: UX/accessibility owner; named person not yet assigned.
- Inherent score: 3 x 4 = 12, High.
- Current controls: Target-setting ADR and automated/manual matrix, state planned.
- Treatment/action owner/due: Select target and representative matrix in WP-02
  before UI implementation; UX/accessibility owner.
- Trigger: Keyboard trap, inaccessible evidence, contrast/reflow failure, or
  missing assistive-technology evidence.
- Contingency: Block affected workflow release and remediate or provide an
  accessible alternative.
- Verification: Automated checks, keyboard/focus/zoom/reflow/manual screen
  reader review, and independent accessibility review.
- Residual: Not assessed; accepting authority is accessibility and product owner.

### R-011 - Source sites change or block extraction

- Cause/event: Page structure, access behavior, or content format changes.
- Consequence/assets: Automatic capture becomes unreliable or misleading,
  while the user still needs a usable fallback.
- Requirements/packages: FR-002, FR-003, SEC-003, NFR-005; WP-03/WP-05.
- Owner: Extension lead; named person not yet assigned.
- Inherent score: 4 x 3 = 12, High.
- Current controls: Generic extraction contract, fixtures, preview/edit, and
  selection/paste fallback, state planned.
- Treatment/action owner/due: Define adapter limitations and fallback
  acceptance before WP-03 release; extension lead.
- Trigger: Extraction regression or approved success threshold breach.
- Contingency: Disable broken adapter, preserve manual capture, and document
  the limitation.
- Verification: Fixture regression suite, representative manual scenarios,
  and fallback end-to-end evidence.
- Residual: Not assessed; accepting authority is extension and product owner.

### R-012 - Export leaks or executes content

- Cause/event: Export includes unexpected fields or CSV cells begin with
  spreadsheet formula markers.
- Consequence/assets: Privacy disclosure or code execution when a file is
  opened by a spreadsheet program.
- Requirements/packages: FR-012, SEC-006, PRIV-004; WP-05.
- Owner: Dashboard lead; named person not yet assigned.
- Inherent score: 3 x 4 = 12, High.
- Current controls: Data classification, explicit schema/preview, neutralization,
  and round-trip tests, state planned.
- Treatment/action owner/due: Freeze export schema and escaping rules before
  WP-05 release; dashboard lead with security owner.
- Trigger: Exported fields exceed the reviewed schema or formula markers execute.
- Contingency: Disable affected format, advise deletion/re-export, and patch
  the encoder.
- Verification: Schema snapshot, malicious-cell fixtures, round-trip tests,
  and security review.
- Residual: Not assessed; accepting authority is security and product owner.

### R-013 - Unsupported technical choices create debt

- Cause/event: Tooling, browser, or backend runtime is selected without
  official support, compatibility, license, security, or update evidence.
- Consequence/assets: Early rework, vulnerabilities, or incompatible release.
- Requirements/packages: NFR-006, SEC-010; WP-02/WP-06/WP-08.
- Owner: Architecture owner; named person not yet assigned.
- Inherent score: 3 x 4 = 12, High.
- Current controls: Time-boxed spike, official-source evidence, and ADR review,
  state planned.
- Treatment/action owner/due: Complete support/license/security review before
  accepting ADR-0001 or ADR-0007; architecture owner.
- Trigger: A choice lacks support horizon, compatibility proof, or update policy.
- Contingency: Replace it before implementation expands and isolate contracts.
- Verification: Support matrix, reproducible spike, dependency/license review,
  and accepted ADR.
- Residual: Not assessed; accepting authority is architecture owner.

### R-014 - Scope drift creates an MVP dependency

- Cause/event: MVP acceptance begins requiring an account, server, AI, or
  network even though the local boundary excludes it.
- Consequence/assets: Increased privacy/security scope, delayed value, and
  invalid acceptance.
- Requirements/packages: NFR-001, SEC-009, PRIV-001, FR-014, FR-015; all packages.
- Owner: Product owner; named person not yet assigned.
- Inherent score: 4 x 3 = 12, High.
- Current controls: Requirement traceability, package gates, and local offline
  acceptance, state planned.
- Treatment/action owner/due: Review every change and move optional features
  to WP-06/WP-07; product owner at each package gate.
- Trigger: MVP criterion references account, server, AI, or network.
- Contingency: Remove the dependency or move it to a later package and
  reapprove the value case.
- Verification: Scope review, offline acceptance scenario, and change record.
- Residual: Not assessed; accepting authority is product owner.

## Current follow-up

Before implementation readiness, assign individual owners, resolve the
repository review/recovery policy, and turn each planned control into a
dated verification task. WP-02 must review all High/Critical entries before
architecture implementation begins.
