# Work-Package Roadmap

Status: Draft - WP-01 source of truth  
Date: 2026-09-17  
Critical-path rule: cloud synchronization and AI are not prerequisites for
the local MVP.

## Dependency map

~~~mermaid
flowchart TD
  WP01[WP-01 scope and governance] --> WP02[WP-02 architecture and security]
  WP02 --> WP03[WP-03 extension capture MVP]
  WP02 --> WP04[WP-04 analysis core and ontology]
  WP03 --> WP05[WP-05 local dashboard and reports]
  WP04 --> WP05
  WP02 --> WP06[WP-06 optional backend and sync]
  WP04 --> WP06
  WP04 --> WP07[WP-07 optional AI assistance]
  WP06 --> WP07
  WP03 --> WP08[WP-08 security and operations]
  WP04 --> WP08
  WP05 --> WP08
  WP06 --> WP08
  WP07 --> WP08
  WP08 --> WP09[WP-09 release candidate and validation]
~~~

WP-03 and WP-04 can proceed in parallel only after WP-02 freezes their
shared contracts. WP-05 requires both. WP-06 and WP-07 remain optional
branches from the deterministic/local foundation.

## Package plan

| Package | Scope | Entry gate | Outputs and exit gate |
|---|---|---|---|
| WP-01 | Discovery, scope, requirements, governance, risks, ADR proposals, security/privacy and quality plans | Approved WP-01 plan and repository inspection | Documentation baseline, acceptance record, and WP-02 handoff |
| WP-02 | Architecture, security foundation, data contracts, packaging, tooling evidence, accessibility target, local-store design | WP-01 source of truth reviewed; decision owners assigned | Accepted architecture/security ADRs, contracts, verification plan, and implementation-ready gates |
| WP-03 | User-initiated Manifest V3 capture, permission boundary, preview input, selection/paste fallback | WP-02 capture contracts and permission/security gates | Tested capture flow with hostile-input and fallback evidence |
| WP-04 | Deterministic bilingual analyzer, ontology, aliases, distinctions, corpus, evaluation | WP-02 data contracts and approved corpus governance | Versioned analyzer/ontology, baseline metrics, error analysis, and release-gate proposal |
| WP-05 | Local dashboard, collections, comparison, corrections, evidence views, export, deletion | WP-03 capture and WP-04 analysis contracts | Accessible end-to-end local workflow with data/export/deletion evidence |
| WP-06 | Optional backend, account/session model, synchronization, authorization, conflicts, deletion propagation | Explicit approval; local MVP remains independent | Authenticated sync with negative authorization and recovery evidence |
| WP-07 | Optional provider-neutral AI assistance and deterministic fallback | Deterministic baseline and WP-06 controls if remote | Consent, schema/evidence validation, budgets, and fallback comparison |
| WP-08 | Security hardening, supply-chain policy, operations, recovery, release automation | Implemented package evidence and accumulated risk review | Operational exercises, hardening evidence, and release gates |
| WP-09 | Representative real-world validation, browser/store readiness, performance, final review | Prior package acceptance and target environments | Go/no-go record, limitations, and release candidate evidence |

## Package handoffs

### WP-01 to WP-02

WP-02 receives the requirements, scope boundary, personas, glossary,
traceability, governance, risk method/register, Proposed ADRs, security and
privacy baseline, accessibility plan, accuracy plan, and test strategy.

WP-02 must return architecture and trust-boundary evidence, a local data
model/migration proposal, extension/dashboard packaging decision, supported
tooling evidence, a specific accessibility target proposal, and updated
risks/ADRs.

### WP-02 to WP-03/WP-04/WP-05

WP-03 needs capture, permission, message, hostile-input, and evidence
contracts. WP-04 needs domain, versioning, corpus, and scoring contracts.
WP-05 needs the stable local data, analysis, correction, export, deletion,
and accessibility contracts from the earlier packages.

### WP-02 to WP-06/WP-07

WP-06 must not become an MVP dependency. It receives the deferred cloud
boundary, export/interchange decision, privacy and authorization
requirements, and local schema contracts. WP-07 requires explicit opt-in,
schema/evidence validation, and a deterministic fallback; it must not replace
the local analyzer.

## Gate rules

- A package cannot start implementation while an upstream contract that could
  invalidate it is unresolved.
- A package cannot declare completion while a Critical or High risk lacks its
  required treatment, contingency, and verification evidence.
- Scope additions that introduce accounts, network transmission, AI, or
  backend URL fetching require a change record and package reapproval.
- Every package updates the requirement traceability, risk register, ADR
  index, limitations, and handoff evidence.
