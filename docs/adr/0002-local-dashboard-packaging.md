# ADR-0002: Local Dashboard Packaging

Status: Proposed  
Date: 2026-09-17  
Owners: Architecture owner, dashboard lead, extension lead  
Deciders: Architecture owner and product owner; named individuals not assigned  
Target package: WP-02  
Related requirements: FR-005, FR-011, NFR-001, SEC-003, PRIV-001  
Related risks: R-002, R-003, R-013, R-014

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
