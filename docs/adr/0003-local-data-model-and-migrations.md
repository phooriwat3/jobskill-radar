# ADR-0003: Local Data Model and Migrations

Status: Proposed  
Date: 2026-09-17  
Owners: Architecture owner, dashboard lead, analysis lead  
Deciders: Architecture owner and privacy owner; named individuals not assigned  
Target package: WP-02  
Related requirements: FR-004, FR-005, FR-008, FR-009, FR-010, FR-013, NFR-003, NFR-005  
Related risks: R-003, R-006, R-012

## Context

The MVP needs local storage for original evidence, edits, derived analysis,
corrections, collections, versions, exports, and deletion. Original evidence
must remain distinct and recoverable. IndexedDB behavior, quotas,
transactions, migrations, offset conventions, and export compatibility are
not yet evidenced.

## Decision scope

This ADR covers identifiers, record boundaries, evidence offsets, local store
layout, versioning, migration, transaction failure, and compatibility. It
does not implement a database schema or select cloud persistence.

## Options considered

### Option A: Domain-separated stores with explicit version

Separates evidence, derived records, corrections, and collections and makes
ownership clear; migration coordination may be more complex.

### Option B: One aggregate store

Can simplify transactions for a captured job; it may increase corruption
blast radius and blur immutable/derived boundaries.

### Option C: Library-defined model

A storage library may reduce repetitive code; its behavior, browser support,
and migration guarantees require independent evidence.

## Evidence required

Define invariants, stable ID rules, Unicode/offset convention, transaction
and interruption behavior, quota limits, migration/backup fixtures, export
compatibility, performance prototype, and supported-browser results.

## Decision

Proposed only. The schema, wrapper, offset convention, and migration plan are
not accepted in WP-01.

## Consequences and tradeoffs

Separating source and derived data supports corrections, recomputation,
deletion, and evidence inspection but requires explicit references and
version compatibility. Every migration must be reversible through a reviewed
export or an equivalent recovery path.

## Security, privacy, accessibility, and operations

Review data minimization, deletion propagation, sensitive URL/text handling,
safe exports, corruption recovery, quota failure, accessible error
messages, and diagnostics that do not expose captured text.

## Validation plan

WP-02 records the data contract and migration matrix. WP-05 supplies fixtures
for save, edit, correction, export, deletion, interrupted upgrade, and
recovery.

## Rollback or revisit triggers

Revisit if a migration can orphan evidence/corrections, a browser changes
transaction behavior, exports cannot recover data, or approved performance
budgets are missed.
