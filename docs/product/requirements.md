# Requirements

Status: Draft - WP-01 source of truth  
Date: 2026-09-17  
Priority vocabulary: MUST is a planned release requirement; it is not a
claim that the requirement is implemented.

Each requirement has a stable identifier. Verification references are planned
evidence locations; no product verification is claimed in WP-01.

## Functional requirements

| ID | Requirement | Priority/release | Planned verification |
|---|---|---|---|
FR-001 | The extension MUST initiate capture only from an explicit user action. | MUST / MVP | WP-03 permission and interaction tests |
FR-002 | Capture MUST support page-derived content, selected text, and manual paste fallback. | MUST / MVP | WP-03 capture fixtures and fallback tests |
FR-003 | The user MUST be able to preview and edit a capture before saving. | MUST / MVP | WP-03/WP-05 end-to-end review journey |
FR-004 | The system MUST store original captured evidence separately from user edits and correction records. | MUST / MVP | WP-02 data contract and WP-05 persistence tests |
FR-005 | The system MUST support local collections and create, read, update, and delete operations for captured jobs. | MUST / MVP | WP-05 local-store integration tests |
FR-006 | The system MUST warn about probable duplicates and MUST allow the user to continue. | MUST / MVP | WP-05 duplicate fixtures and UX test |
FR-007 | Deterministic analysis MUST classify the agreed qualification categories in Thai and English. | MUST / MVP | WP-04 corpus evaluation by language/category |
FR-008 | Every reported qualification MUST reference at least one source job and evidence span or snippet. | MUST / MVP | WP-04/WP-05 evidence-link contract tests |
FR-009 | Frequency MUST count a canonical item at most once per job. | MUST / MVP | WP-04 unique-per-job fixtures |
FR-010 | Users MUST be able to accept, reject, add, and remap results without changing original evidence. | MUST / MVP | WP-05 correction and immutability tests |
FR-011 | The dashboard MUST filter jobs/results and compare selected jobs. | MUST / MVP | WP-05 workflow and comparison tests |
FR-012 | Users MUST be able to export documented JSON and CSV representations. | MUST / MVP | WP-05 schema, escaping, and round-trip tests |
FR-013 | Users MUST be able to delete individual jobs, collections, and all local product data. | MUST / MVP | WP-05 deletion and recovery tests |
FR-014 | Optional synchronization MUST preserve authorization, deletion, version, and conflict semantics. | MUST / WP-06 | WP-06 multi-user and conflict tests |
FR-015 | Optional AI assistance MUST require opt-in and MUST fall back to deterministic results. | MUST / WP-07 | WP-07 consent, outage, and evidence tests |

## Non-functional and operational requirements

| ID | Requirement | Priority/release | Planned verification |
|---|---|---|---|
NFR-001 | Core MVP functions MUST work without network access after installation. | MUST / MVP | WP-03/WP-05 offline scenario and network observation |
NFR-002 | Deterministic analysis MUST produce reproducible results for the same input, ontology, and analyzer version. | MUST / MVP | WP-04 golden output and stable serialization |
NFR-003 | Local schema and exports MUST be versioned and migratable. | MUST / MVP | WP-02 migration contract and fixtures |
NFR-004 | Supported data volumes MUST remain usable within approved latency and storage budgets. | MUST / MVP | WP-02/WP-05 volume study after budgets are approved |
NFR-005 | Failures MUST preserve previously committed local records and provide actionable, non-sensitive messages. | MUST / MVP | WP-02/WP-05 fault-injection and recovery scenarios |
NFR-006 | Browser/tooling dependencies MUST use supported releases and reproducible lockfiles. | MUST / release | WP-02 support, license, security, and reproducibility review |
NFR-007 | Cloud components, when introduced, MUST define service objectives, observability, restore targets, and incident ownership before production use. | MUST / WP-06/WP-08 | WP-06/WP-08 operational design and exercises |

## Security requirements

| ID | Requirement | Priority/release | Planned verification |
|---|---|---|---|
SEC-001 | Captured page content MUST be treated as untrusted data and never interpreted as privileged instructions or executable markup. | MUST / MVP | WP-03 hostile-content and rendering tests |
SEC-002 | UI rendering MUST use safe text rendering; unavoidable HTML parsing requires an approved sanitizer boundary and adversarial tests. | MUST / MVP | WP-02/WP-03 security review and fixtures |
SEC-003 | Extension permissions and host access MUST be the minimum justified by documented capture flows. | MUST / MVP | WP-02 permission ADR and WP-03 manifest review |
SEC-004 | Extension messages MUST have explicit schemas, sender/context validation, size limits, and deny-by-default handling. | MUST / MVP | WP-02 contract and WP-03 negative tests |
SEC-005 | Stored or opened URLs MUST be validated against an allowlist of required schemes; dangerous schemes MUST not become executable links. | MUST / MVP | WP-03/WP-05 URL validation tests |
SEC-006 | Imports/exports and future AI responses MUST be schema-validated with bounded sizes and safe failure behavior. | MUST / MVP/WP-07 | WP-05 export/import tests and WP-07 response tests |
SEC-007 | Secrets MUST NOT be shipped in client bundles or committed to the repository. | MUST / release | WP-02/WP-08 secret scanning and build review |
SEC-008 | Future cloud APIs MUST authenticate requests and enforce object authorization independently for every operation. | MUST / WP-06 | WP-06 negative authorization tests |
SEC-009 | The product MUST NOT fetch source job URLs server-side or circumvent access controls. | MUST / all | Architecture review and network-observation evidence |
SEC-010 | Dependencies and builds MUST be subject to agreed provenance, vulnerability, and update policies before release. | MUST / release | WP-02/WP-08 supply-chain and update review |

## Privacy requirements

| ID | Requirement | Priority/release | Planned verification |
|---|---|---|---|
PRIV-001 | The MVP MUST default to local-only processing and storage with no account or telemetry. | MUST / MVP | WP-02 data-flow and offline/network tests |
PRIV-002 | The capture preview MUST make content and source metadata to be stored inspectable before save. | MUST / MVP | WP-03 preview workflow test |
PRIV-003 | Network transmission of captured content MUST require a separately described, explicit opt-in purpose. | MUST / later | WP-06/WP-07 consent and network tests |
PRIV-004 | Users MUST be able to export and delete local data, including derived data and corrections. | MUST / MVP | WP-05 export/deletion tests |
PRIV-005 | Data inventory, purpose, location, retention behavior, and deletion semantics MUST be documented for each release. | MUST / all | Release checklist and privacy review |
PRIV-006 | Corpus examples MUST be licensed or permitted, minimized, and scrubbed of personal or unnecessary sensitive data before repository inclusion. | MUST / WP-04 | Corpus register and provenance review |
PRIV-007 | Privacy documentation MUST distinguish product behavior from unverified legal-compliance claims. | MUST / all | Documentation review |

## Accessibility requirements

| ID | Requirement | Priority/release | Planned verification |
|---|---|---|---|
A11Y-001 | All core workflows MUST be operable with a keyboard and expose logical focus order and visible focus. | MUST / MVP | WP-05 keyboard and focus matrix |
A11Y-002 | Controls, statuses, errors, evidence, confidence, and corrections MUST have programmatic names/semantics and MUST not rely on color alone. | MUST / MVP | Automated checks plus manual semantics review |
A11Y-003 | Text and interactive elements MUST meet the approved contrast and target-size criteria. | MUST / MVP | Target-setting ADR plus automated/manual checks |
A11Y-004 | Dashboard layouts MUST remain usable at agreed viewport sizes and browser zoom levels. | MUST / MVP | WP-05 responsive and zoom matrix |
A11Y-005 | Thai and English text, long tokens, and mixed-language content MUST render and reflow without loss of access to actions or evidence. | MUST / MVP | WP-04/WP-05 mixed-language fixtures and manual review |
A11Y-006 | WP-02 MUST recommend a specific WCAG conformance target and browser/assistive-technology test matrix based on distribution and stakeholder approval. | MUST / WP-02 | Accepted ADR and test matrix |

## Accuracy and evidence requirements

| ID | Requirement | Priority/release | Planned verification |
|---|---|---|---|
ACC-001 | The ontology, analyzer rules, corpus, annotation guide, and evaluation output MUST be version-controlled together or by explicit compatible versions. | MUST / WP-04 | Version manifest and review |
ACC-002 | Evaluation MUST report per-category and aggregate precision, recall, and F1, with language slices and support counts. | MUST / WP-04 | Evaluation report |
ACC-003 | Required/preferred classification and evidence-span correctness MUST be evaluated separately from entity recognition. | MUST / WP-04 | Separate scoring report |
ACC-004 | Exact-match and documented canonical-equivalence rules MUST be fixed before scoring a corpus version. | MUST / WP-04 | Frozen scoring specification |
ACC-005 | Train/development/test or authoring/evaluation separation MUST prevent tuning directly against the final evaluation set. | MUST / WP-04 | Split manifest and leakage review |
ACC-006 | Accuracy targets MUST be adopted only after baseline measurement on a representative, quality-reviewed bilingual corpus. | MUST / WP-04 | Baseline report and decision record |
ACC-007 | Reports MUST disclose dataset version, sample composition, exclusions, confidence intervals or uncertainty where appropriate, and known limitations. | MUST / WP-04 | Evaluation report review |
ACC-008 | No UI or documentation may imply perfect, exhaustive, or universally representative extraction. | MUST / all | Product and documentation review |

## Verification language

Planned describes future evidence. Implemented describes a change that exists.
Tested requires a recorded test execution. Verified requires review of the
relevant evidence by the accountable reviewer. WP-01 records documentation
checks and plans; it does not claim product verification.
