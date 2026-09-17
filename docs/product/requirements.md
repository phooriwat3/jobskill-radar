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
FR-001 <a id="fr-001"></a> | The extension MUST initiate capture only from an explicit user action. | MUST / MVP | WP-03 permission and interaction tests |
FR-002 <a id="fr-002"></a> | Capture MUST support page-derived content, selected text, and manual paste fallback. | MUST / MVP | WP-03 capture fixtures and fallback tests |
FR-003 <a id="fr-003"></a> | The user MUST be able to preview and edit a capture before saving. | MUST / MVP | WP-03/WP-05 end-to-end review journey |
FR-004 <a id="fr-004"></a> | The system MUST store original captured evidence separately from user edits and correction records. | MUST / MVP | WP-02 data contract and WP-05 persistence tests |
FR-005 <a id="fr-005"></a> | The system MUST support local collections and create, read, update, and delete operations for captured jobs. | MUST / MVP | WP-05 local-store integration tests |
FR-006 <a id="fr-006"></a> | The system MUST warn about probable duplicates and MUST allow the user to continue. | MUST / MVP | WP-05 duplicate fixtures and UX test |
FR-007 <a id="fr-007"></a> | Deterministic analysis MUST classify the agreed qualification categories in Thai and English. | MUST / MVP | WP-04 corpus evaluation by language/category |
FR-008 <a id="fr-008"></a> | Every reported qualification MUST reference at least one source job and evidence span or snippet. | MUST / MVP | WP-04/WP-05 evidence-link contract tests |
FR-009 <a id="fr-009"></a> | Frequency MUST count a canonical item at most once per job. | MUST / MVP | WP-04 unique-per-job fixtures |
FR-010 <a id="fr-010"></a> | Users MUST be able to accept, reject, add, and remap results without changing original evidence. | MUST / MVP | WP-05 correction and immutability tests |
FR-011 <a id="fr-011"></a> | The dashboard MUST filter jobs/results and compare selected jobs. | MUST / MVP | WP-05 workflow and comparison tests |
FR-012 <a id="fr-012"></a> | Users MUST be able to export documented JSON and CSV representations. Import is not an MVP requirement. | MUST / MVP | WP-05 export schema, escaping, and round-trip tests |
FR-013 <a id="fr-013"></a> | Users MUST be able to delete individual jobs, collections, and all local product data. | MUST / MVP | WP-05 deletion and recovery tests |
FR-014 <a id="fr-014"></a> | Optional synchronization MUST preserve authorization, deletion, version, and conflict semantics. | MUST / WP-06 | WP-06 multi-user and conflict tests |
FR-015 <a id="fr-015"></a> | Optional AI assistance MUST require opt-in and MUST fall back to deterministic results. | MUST / WP-07 | WP-07 consent, outage, and evidence tests |

## Non-functional and operational requirements

| ID | Requirement | Priority/release | Planned verification |
|---|---|---|---|
NFR-001 <a id="nfr-001"></a> | Core MVP functions MUST work without network access after installation. | MUST / MVP | WP-03/WP-05 offline scenario and network observation |
NFR-002 <a id="nfr-002"></a> | Deterministic analysis MUST produce reproducible results for the same input, ontology, and analyzer version. | MUST / MVP | WP-04 golden output and stable serialization |
NFR-003 <a id="nfr-003"></a> | Local schema and exports MUST be versioned and migratable. | MUST / MVP | WP-02 migration contract and fixtures |
NFR-004 <a id="nfr-004"></a> | Supported data volumes MUST remain usable within approved latency and storage budgets. | MUST / MVP | WP-02/WP-05 volume study after budgets are approved |
NFR-005 <a id="nfr-005"></a> | Failures MUST preserve previously committed local records and provide actionable, non-sensitive messages. | MUST / MVP | WP-02/WP-05 fault-injection and recovery scenarios |
NFR-006 <a id="nfr-006"></a> | Browser/tooling dependencies MUST use supported releases and reproducible lockfiles. | MUST / release | WP-02 support, license, security, and reproducibility review |
NFR-007 <a id="nfr-007"></a> | Cloud components, when introduced, MUST define service objectives, observability, restore targets, and incident ownership before production use. | MUST / WP-06/WP-08 | WP-06/WP-08 operational design and exercises |

## Security requirements

| ID | Requirement | Priority/release | Planned verification |
|---|---|---|---|
SEC-001 <a id="sec-001"></a> | Captured page content MUST be treated as untrusted data and never interpreted as privileged instructions or executable markup. | MUST / MVP | WP-03 hostile-content and rendering tests |
SEC-002 <a id="sec-002"></a> | UI rendering MUST use safe text rendering; unavoidable HTML parsing requires an approved sanitizer boundary and adversarial tests. | MUST / MVP | WP-02/WP-03 security review and fixtures |
SEC-003 <a id="sec-003"></a> | Extension permissions and host access MUST be the minimum justified by documented capture flows. | MUST / MVP | WP-02 permission ADR and WP-03 manifest review |
SEC-004 <a id="sec-004"></a> | Extension messages MUST have explicit schemas, sender/context validation, size limits, and deny-by-default handling. | MUST / MVP | WP-02 contract and WP-03 negative tests |
SEC-005 <a id="sec-005"></a> | Stored or opened URLs MUST be validated against an allowlist of required schemes; dangerous schemes MUST not become executable links. | MUST / MVP | WP-03/WP-05 URL validation tests |
SEC-006 <a id="sec-006"></a> | MVP exports and future AI responses MUST be schema-validated with bounded sizes and safe failure behavior. Any import/interchange remains deferred unless separately approved. | MUST / MVP/WP-07 | WP-05 export tests and WP-07 response tests; approved-import tests only if authorized |
SEC-007 <a id="sec-007"></a> | Secrets MUST NOT be shipped in client bundles or committed to the repository. | MUST / release | WP-02/WP-08 secret scanning and build review |
SEC-008 <a id="sec-008"></a> | Future cloud APIs MUST authenticate requests and enforce object authorization independently for every operation. | MUST / WP-06 | WP-06 negative authorization tests |
SEC-009 <a id="sec-009"></a> | The product MUST NOT fetch source job URLs server-side or circumvent access controls. | MUST / all | Architecture review and network-observation evidence |
SEC-010 <a id="sec-010"></a> | Dependencies and builds MUST be subject to agreed provenance, vulnerability, and update policies before release. | MUST / release | WP-02/WP-08 supply-chain and update review |

## Privacy requirements

| ID | Requirement | Priority/release | Planned verification |
|---|---|---|---|
PRIV-001 <a id="priv-001"></a> | The MVP MUST default to local-only processing and storage with no account or telemetry. | MUST / MVP | WP-02 data-flow and offline/network tests |
PRIV-002 <a id="priv-002"></a> | The capture preview MUST make content and source metadata to be stored inspectable before save. | MUST / MVP | WP-03 preview workflow test |
PRIV-003 <a id="priv-003"></a> | Network transmission of captured content MUST require a separately described, explicit opt-in purpose. | MUST / later | WP-06/WP-07 consent and network tests |
PRIV-004 <a id="priv-004"></a> | Users MUST be able to export and delete local data, including derived data and corrections. | MUST / MVP | WP-05 export/deletion tests |
PRIV-005 <a id="priv-005"></a> | Data inventory, purpose, location, retention behavior, and deletion semantics MUST be documented for each release. | MUST / all | Release checklist and privacy review |
PRIV-006 <a id="priv-006"></a> | Corpus examples MUST be licensed or permitted, minimized, and scrubbed of personal or unnecessary sensitive data before repository inclusion. | MUST / WP-04 | Corpus register and provenance review |
PRIV-007 <a id="priv-007"></a> | Privacy documentation MUST distinguish product behavior from unverified legal-compliance claims. | MUST / all | Documentation review |

## Accessibility requirements

| ID | Requirement | Priority/release | Planned verification |
|---|---|---|---|
A11Y-001 <a id="a11y-001"></a> | All core workflows MUST be operable with a keyboard and expose logical focus order and visible focus. | MUST / MVP | WP-05 keyboard and focus matrix |
A11Y-002 <a id="a11y-002"></a> | Controls, statuses, errors, evidence, confidence, and corrections MUST have programmatic names/semantics and MUST not rely on color alone. | MUST / MVP | Automated checks plus manual semantics review |
A11Y-003 <a id="a11y-003"></a> | Text and interactive elements MUST meet the approved contrast and target-size criteria. | MUST / MVP | Target-setting ADR plus automated/manual checks |
A11Y-004 <a id="a11y-004"></a> | Dashboard layouts MUST remain usable at agreed viewport sizes and browser zoom levels. | MUST / MVP | WP-05 responsive and zoom matrix |
A11Y-005 <a id="a11y-005"></a> | Thai and English text, long tokens, and mixed-language content MUST render and reflow without loss of access to actions or evidence. | MUST / MVP | WP-04/WP-05 mixed-language fixtures and manual review |
A11Y-006 <a id="a11y-006"></a> | WP-02 MUST recommend a specific WCAG conformance target and browser/assistive-technology test matrix based on distribution and stakeholder approval. | MUST / WP-02 | Accepted ADR and test matrix |

## Accuracy and evidence requirements

| ID | Requirement | Priority/release | Planned verification |
|---|---|---|---|
ACC-001 <a id="acc-001"></a> | The ontology, analyzer rules, corpus, annotation guide, and evaluation output MUST be version-controlled together or by explicit compatible versions. | MUST / WP-04 | Version manifest and review |
ACC-002 <a id="acc-002"></a> | Evaluation MUST report per-category and aggregate precision, recall, and F1, with language slices and support counts. | MUST / WP-04 | Evaluation report |
ACC-003 <a id="acc-003"></a> | Required/preferred classification and evidence-span correctness MUST be evaluated separately from entity recognition. | MUST / WP-04 | Separate scoring report |
ACC-004 <a id="acc-004"></a> | Exact-match and documented canonical-equivalence rules MUST be fixed before scoring a corpus version. | MUST / WP-04 | Frozen scoring specification |
ACC-005 <a id="acc-005"></a> | Train/development/test or authoring/evaluation separation MUST prevent tuning directly against the final evaluation set. | MUST / WP-04 | Split manifest and leakage review |
ACC-006 <a id="acc-006"></a> | Accuracy targets MUST be adopted only after baseline measurement on a representative, quality-reviewed bilingual corpus. | MUST / WP-04 | Baseline report and decision record |
ACC-007 <a id="acc-007"></a> | Reports MUST disclose dataset version, sample composition, exclusions, confidence intervals or uncertainty where appropriate, and known limitations. | MUST / WP-04 | Evaluation report review |
ACC-008 <a id="acc-008"></a> | No UI or documentation may imply perfect, exhaustive, or universally representative extraction. | MUST / all | Product and documentation review |

## Verification language

Planned describes future evidence. Implemented describes a change that exists.
Tested requires a recorded test execution. Verified requires review of the
relevant evidence by the accountable reviewer. WP-01 records documentation
checks and plans; it does not claim product verification.
