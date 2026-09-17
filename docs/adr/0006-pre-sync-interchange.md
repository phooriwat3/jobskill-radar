# ADR-0006: Pre-Sync Export and Import Interchange

Status: Proposed  
Date: 2026-09-17  
Owners: Architecture owner, dashboard lead, privacy owner  
Deciders: Architecture and product owners; named individuals not assigned  
Target package: WP-02/WP-05  
Related requirements: FR-012, FR-013, FR-014, NFR-003, SEC-006, PRIV-004  
Related risks: R-003, R-006, R-012

## Context

Users may need a portable local backup or migration path before optional
cloud synchronization exists. Export/import can also create injection,
privacy, version, and conflict risks. The product already plans JSON and CSV
export, but interchange semantics are not decided.

## Decision scope

This ADR decides whether a versioned import/export interchange is supported
before WP-06 and which data, identity, deletion, and compatibility semantics
it carries. It does not authorize cloud sync.

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
round-trip/security prototype evidence, deletion/correction semantics, and
support cost. Link the result to the local data model ADR.

## Decision

Proposed only. WP-01 does not choose export/import support or a file schema.

## Consequences and tradeoffs

Interchange improves user control but creates a long-lived compatibility
surface and import attack boundary. Export fields must be visible and
minimized; import must not overwrite original evidence silently.

## Security, privacy, accessibility, and operations

Review size limits, schema validation, unsafe URLs, CSV formulas, sensitive
fields, accessible errors, deletion semantics, and recovery guidance.

## Validation plan

WP-05 records a schema, malicious fixtures, round-trip results, version
compatibility, correction behavior, and deletion tests.

## Rollback or revisit triggers

Revisit if import cannot preserve evidence/correction boundaries, a schema
cannot migrate safely, or export exposes fields users did not approve.
