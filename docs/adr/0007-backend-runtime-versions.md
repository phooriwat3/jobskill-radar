# ADR-0007: Optional Backend Runtime Versions

Status: Proposed
Date: 2026-09-17
Owners: Architecture owner, backend security owner, operations owner
Deciders: Architecture and product owners; named individuals not assigned
Target package: WP-06
Related requirements: NFR-006, NFR-007, SEC-008, SEC-010, PRIV-003
Related risks: R-007, R-013, R-014
Related ADRs: [ADR-0001](0001-frontend-workspace-and-tooling.md), [ADR-0008](0008-cloud-authentication.md)
Evidence links: [ADR template](template.md), [ADR index](README.md), [Roadmap](../roadmap/work-packages.md), [Risk register](../risks/risk-register.md)

## Context

The master plan mentions Java 21 and Spring Boot 3.x for a possible later
backend. The local MVP does not require a backend. Runtime versions are
time-sensitive and must be selected using evidence available at WP-06
planning time.

## Decision scope

This ADR covers optional backend runtime and framework support. It does not
create a server, dependency manifest, deployment, or MVP requirement.

## Options considered

### Option A: Java 21 with a currently supported Spring Boot 3.x line

Could align with the planned backend direction; support and compatibility
must be checked at the time of decision.

### Option B: Another supported Java/Spring line

May provide a longer support horizon or team compatibility; it changes the
planned runtime assumption.

### Option C: No backend

Keeps the product local-only; it does not support optional synchronization.

## Evidence required

At WP-06 planning time, collect official vendor/Spring support dates,
compatibility/BOM, security advisories, PostgreSQL/deployment compatibility,
team/runtime constraints, and a reproducible prototype. Record the
operating owner, upgrade policy, and recovery targets.

## Decision

Proposed only. Java 21 and Spring Boot 3.x are not accepted versions and are
not MVP dependencies.

## Consequences and tradeoffs

Deferral avoids stale support claims and prevents a backend from entering the
local critical path. It means cloud planning cannot reuse this ADR without
fresh evidence.

## Security, privacy, accessibility, and operations

Review dependency provenance, patch/update process, authentication and
authorization boundaries, logging minimization, restore behavior, and
operational ownership.

## Validation plan

WP-06 records the official support matrix, prototype build, dependency
review, security review, deployment evidence, and accepted runtime decision.

## Rollback or revisit triggers

Revisit when support or security status changes, the deployment target
changes, a runtime cannot meet recovery objectives, or the backend is removed.
