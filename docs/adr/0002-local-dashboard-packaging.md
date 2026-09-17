# ADR-0002: Local Dashboard Packaging

Status: Proposed
Date: 2026-09-17
Owners: Architecture owner, dashboard lead, extension lead
Deciders: Architecture owner and product owner; named individuals not assigned
Target package: WP-02
Related requirements: [FR-005](../product/requirements.md#fr-005), [FR-011](../product/requirements.md#fr-011), [NFR-001](../product/requirements.md#nfr-001), [SEC-003](../product/requirements.md#sec-003), [PRIV-001](../product/requirements.md#priv-001)
Related risks: [R-002](../risks/risk-register.md#r-002), [R-003](../risks/risk-register.md#r-003), [R-013](../risks/risk-register.md#r-013), [R-014](../risks/risk-register.md#r-014)
Related ADRs: [ADR-0001](0001-frontend-workspace-and-tooling.md), [ADR-0003](0003-local-data-model-and-migrations.md), [ADR-0009](0009-accessibility-target-and-matrix.md)
Evidence links: [ADR template](template.md), [ADR index](README.md), [Product brief](../product/product-brief.md), [Risk register](../risks/risk-register.md)

## Context

The local dashboard must use the same local dataset as capture and remain
useful without a backend or required network. Packaging affects extension
permissions, CSP, IndexedDB sharing, install/update UX, accessibility,
testing, and migration.

## Decision scope

This ADR decides whether the first dashboard is an extension page, a
separately served local web app, or a deliberately bounded hybrid. It does
not decide the data model or cloud architecture.

## Options considered

### Option A: Extension-bundled page

Strong local/offline and permission alignment; potentially simpler storage
sharing. It may constrain navigation, update, and larger dashboard UX.

### Option B: Separately served local web app

Flexible dashboard development and browser navigation; may require a local
server, introduce origin/storage boundaries, and create an unwanted network
or installation dependency.

### Option C: Bounded hybrid

Capture and store remain in the extension while the dashboard is exposed
through an explicitly controlled local surface. It may require more contracts
and boundary testing.

## Evidence required

Compare offline journeys, permissions/CSP, storage sharing, install/update,
accessibility/testing, browser support, failure behavior, migration path, and
user understanding. Record a prototype or design spike before acceptance.

## Decision

Proposed only. No packaging option is accepted in WP-01.

## Consequences and tradeoffs

The decision must keep local MVP acceptance independent of accounts and cloud
services. A separate server is not acceptable merely because it is convenient
if it makes network access or URL fetching a hidden dependency.

## Security, privacy, accessibility, and operations

Review origin isolation, message validation, CSP, permission minimization,
local data exposure, safe rendering, keyboard navigation, zoom/reflow,
upgrade/recovery, and support burden.

## Validation plan

WP-02 records the offline comparison, storage/permission evidence, target
browser results, accessibility checks, and reviewed recommendation.

## Rollback or revisit triggers

Revisit if storage sharing is unreliable, the chosen packaging needs
unapproved permissions/network, blocks accessible workflows, or prevents
recoverable upgrades.
