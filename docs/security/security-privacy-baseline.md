# Security and Privacy Baseline

Status: Preliminary - WP-01 planning baseline
Date: 2026-09-17
Owners: Security owner and privacy owner; named individuals not assigned

This document describes planned boundaries and evidence needs. It does not
claim that a product control, legal compliance obligation, or security test
has been completed.

## Security and privacy principles

- Capture is explicit and user initiated.
- Page text, pasted text, URLs, exports, separately approved future imports,
  and future model output are untrusted data.
- Original evidence is separate from edits, analysis, corrections, and
  exports.
- The MVP is local-only by default and must remain useful without a network,
  account, cloud, telemetry, or AI provider.
- Source URLs are references only; no backend fetches them or bypasses access
  controls.
- Permissions, host access, messages, schemas, sizes, and URLs are
  deny-by-default and allowlisted where applicable.
- Transmission of captured content requires a separate documented purpose and
  explicit opt-in.
- Privacy behavior is documented separately from unverified legal claims.

## Preliminary asset and data inventory

Retention, exact fields, and deletion semantics remain design work for WP-02
and WP-05. The default MVP transmission is none.

| Asset/data | Source and purpose | Planned location | Default transmission | Deletion/retention question | Current state |
|---|---|---|---|---|---|
| Page-derived text | Visible job content captured after user action | Local capture flow, then local store | None | Delete with captured job; define partial-failure behavior | Planned |
| Selected/pasted text | User-selected or manually supplied fallback | Local capture flow, then local store | None | Delete with captured job | Planned |
| Source URL/title/metadata | Context for evidence and navigation | Local captured-job record | None | Delete with captured job; validate URL schemes | Planned |
| Original evidence | Exact accepted job text/metadata used as source truth | Versioned local store | None | Immutable until explicit deletion; define backup behavior | Planned |
| Analysis text and source digest | Exact immutable job-text value accepted when the job is saved and the SHA-256 digest of its exact UTF-8 bytes | Versioned local store | None | Delete with original evidence; digest detects mismatched spans | Planned |
| Edited capture fields | User organization and display metadata; not analyzer input | Separate local record/overlay | None | Delete with related job | Planned |
| Derived analysis | Canonical items, categories, confidence, evidence spans, analyzer version | Local derived records | None | Delete/recompute with related job | Planned |
| Corrections | User accept/reject/add/remap decisions | Separate local correction records | None | Delete with related job and exports | Planned |
| Collections | User grouping of captured jobs | Local store | None | Individual/all-data deletion | Planned |
| JSON/CSV exports | User-requested backup/report; export only in MVP | User-selected destination | Only if user moves it | User controls external copy; product cannot revoke copies | Planned |
| Corpus samples/annotations | Permitted, minimized evaluation material | Versioned project data when approved | None by default | Permission, retention, and removal register required | Proposed |
| Future sync data | Optional later cloud copy | WP-06 service if approved | Opt-in only | Account/object deletion propagation required | Deferred |
| Future AI request/response | Optional provider-assisted analysis | WP-07 provider boundary if approved | Opt-in only | Provider retention and deletion must be disclosed | Deferred |

## Trust boundaries

~~~mermaid
flowchart LR
  Page[User-viewed page and selected text] -->|explicit action| Capture[Extension capture boundary]
  Paste[Manual paste fallback] --> Capture
  Capture -->|validated untrusted data| Local[Local versioned store]
  Local --> Dashboard[Local dashboard]
  Dashboard --> Export[User-requested export]
  Local -. opt-in, later .-> Sync[Future cloud sync]
  Local -. opt-in, later .-> AI[Future AI provider]
  Sync -.-> Auth[Future identity and authorization]
~~~

The dashed paths are not part of the MVP. Import/interchange behavior and
invalid-import testing are also not part of the MVP unless separately
approved. Each later crossing needs a separate schema, consent, threat model,
size limit, failure policy, and verification record.

## Analysis-text and evidence contract

Deterministic analysis reads exactly one field: the immutable job-text value
accepted when the job is saved from page-derived relevant text, selected text,
or manual paste after preview. It does not read source URL, page title,
timestamps, collection labels, user notes, later metadata edits, or correction text;
only text accepted into that job-text value before save can be analyzed.

The exact job-text string is encoded as UTF-8 without trimming, Unicode
normalization, line-ending conversion, or locale-dependent transformation.
Each result stores a zero-based, end-exclusive UTF-8 byte range and the
SHA-256 source digest of the exact analysis text. A viewer must reject or flag
a span when the digest does not match. This makes offsets reproducible across
supported runtimes and keeps them traceable to immutable original evidence.

## Boundary questions for WP-02

1. Which extension contexts can read page content, and how is sender/context
   identity validated?
2. Which permissions and host patterns are essential for each capture journey?
3. Which fields are stored before preview, at save, and after correction?
4. What URL schemes are required, and how are dangerous schemes displayed?
5. How will WP-02 implement and test the documented UTF-8 byte-offset and
   SHA-256 source-digest convention?
6. How are IndexedDB upgrades interrupted, recovered, and tested?
7. What diagnostics can be recorded without exposing job text or URLs?
8. How are MVP exports bounded, schema-validated, and protected from CSV
   formula execution? What separate approval would be required for import?
9. What deletion means for derived data, corrections, backups, and future
   synchronized copies?
10. What user consent and provider retention disclosures would be required
    before any sync or AI path?

## Threat-model plan

WP-02 should conduct a structured workshop covering:

- Malicious or instruction-like page text and pasted content.
- HTML/script injection, unsafe URLs, extension message confusion, and
  oversized payloads.
- Permission/host overreach and cross-context access.
- Local store exposure, corruption, migration, export, and deletion.
- CSV/JSON injection and any separately approved import behavior.
- Corpus provenance, personal-data leakage, annotation access, and leakage
  between authoring and evaluation splits.
- Future sync authentication, object authorization, conflicts, recovery, and
  deletion propagation.
- Future AI transmission, provider retention, fabricated output, evidence
  validation, budgets, and deterministic fallback.

The workshop output must include assets, actors, trust boundaries, abuse
cases, controls, verification tasks, residual risk, and owners. Documentation
of a threat is not verification of its control.

## Baseline control plan

| Boundary | Planned control | Requirement links | Evidence needed |
|---|---|---|---|
| Page/content | Safe text rendering; no privileged interpretation | SEC-001, SEC-002 | Hostile-content fixtures and review |
| Extension permissions | Minimum journey-based permission budget | SEC-003, PRIV-001 | Permission matrix and manifest review |
| Messages | Explicit schema, sender/context validation, size limits, deny-by-default | SEC-004 | Contract and negative tests |
| URLs | Required-scheme allowlist; no executable dangerous links | SEC-005, SEC-009 | URL fixtures and network observation |
| Local data | Separate original/derived/correction records; versioned migration | FR-004, NFR-003, PRIV-004 | Data contract, migration, deletion tests |
| MVP export | Bounded schema, visible fields, safe CSV handling; import is deferred | SEC-006, FR-012 | Malicious-cell and export round-trip tests |
| Secrets/dependencies | No client secrets; provenance/update policy | SEC-007, SEC-010 | Build/secret/dependency review |
| Future sync | Authentication plus independent object authorization | SEC-008, FR-014 | Multi-user negative tests |
| Future AI | Explicit opt-in, schema/evidence validation, deterministic fallback | FR-015, PRIV-003 | Consent, outage, and comparison evidence |

All controls above are planned, not implemented or verified.

## Privacy review questions

- Is every captured field necessary for the stated user journey?
- Does the preview show exactly what will be saved?
- Is local retention understandable and user-controlled?
- Does delete remove original, derived, correction, collection, and local
  export references as documented?
- Are third-party advertisements and personal data permitted and minimized
  before corpus use?
- Are network, sync, and AI purposes separate, optional, and visible?
- Do documents avoid claiming legal compliance without jurisdiction-specific
  review?

## Required downstream evidence

WP-02 returns the architecture/data-flow/trust-boundary and threat models.
WP-03 returns permission, message, hostile-input, URL, capture, manual-fallback,
and analysis-text evidence.
WP-04 returns corpus provenance/minimization and ontology evidence. WP-05
returns local-store, correction, export-only, deletion, and accessibility
evidence. Any import evidence requires separate approval.
WP-06/WP-07 return authorization, consent, provider, and fallback evidence if
those packages are approved.
