# ADR-0006: Pre-Sync Export and Import Interchange

Status: Proposed
Date: 2026-09-17
Owners: Architecture owner, dashboard lead, privacy owner
Deciders: Architecture and product owners; named individuals not assigned
Target package: WP-02/WP-05
Related requirements: [FR-012](../product/requirements.md#fr-012), [FR-013](../product/requirements.md#fr-013), [FR-014](../product/requirements.md#fr-014), [NFR-003](../product/requirements.md#nfr-003), [SEC-006](../product/requirements.md#sec-006), [PRIV-004](../product/requirements.md#priv-004)
Related risks: [R-003](../risks/risk-register.md#r-003), [R-006](../risks/risk-register.md#r-006), [R-012](../risks/risk-register.md#r-012)
Related ADRs: [ADR-0003](0003-local-data-model-and-migrations.md), [ADR-0008](0008-cloud-authentication.md)
Evidence links: [ADR template](template.md), [ADR index](README.md), [Requirements](../product/requirements.md), [Security/privacy baseline](../security/security-privacy-baseline.md)

## Context

Users may need a portable local backup or migration path before optional
cloud synchronization exists. Export/import can also create injection,
privacy, version, and conflict risks. The product already plans JSON and CSV
export, but interchange semantics are not decided.

## Decision scope

The MVP supports export only. This ADR decides whether a separately approved
versioned import/interchange is supported before WP-06 and which data,
identity, deletion, and compatibility semantics it carries. It does not
authorize cloud sync or add import to MVP scope.

## Options considered

### Option A: Export only

Smaller attack surface and implementation scope; no restore or migration path.

### Option B: Versioned JSON interchange

Supports backup and migration with schemas and bounded validation; requires
careful identity and privacy semantics.

### Option C: JSON plus CSV

Supports portability and analysis; CSV is less expressive and needs formula
injection defenses.

## Evidence required

Gather user backup/migration needs, privacy/schema-version risks,
export round-trip/security prototype evidence, deletion/correction semantics, and
support cost. Invalid-import tests are deferred and may be added only after
separate approval. Link the result to the local data model ADR.

## Decision

Proposed only. WP-01 accepts the export-only MVP boundary. Import/interchange
remains deferred unless a separate approval and change record/ADR authorizes
it.

## Consequences and tradeoffs

Interchange improves user control but creates a long-lived compatibility
surface and import attack boundary. Export fields must be visible and
minimized; import must not overwrite original evidence silently.

## Security, privacy, accessibility, and operations

Review size limits, schema validation, unsafe URLs, CSV formulas, sensitive
fields, accessible errors, deletion semantics, and recovery guidance.

## Validation plan

WP-05 records the export schema, malicious fixtures, export round-trip results,
version compatibility, correction behavior, and deletion tests. Import
behavior and invalid-import tests remain deferred unless separately approved.

## Rollback or revisit triggers

Revisit if import cannot preserve evidence/correction boundaries, a schema
cannot migrate safely, or export exposes fields users did not approve.
