# ADR-0008: Optional Cloud Authentication and Sessions

Status: Proposed
Date: 2026-09-17
Owners: Backend security owner, privacy owner, architecture owner
Deciders: Security/privacy and product owners; named individuals not assigned
Target package: WP-06
Related requirements: [FR-014](../product/requirements.md#fr-014), [NFR-007](../product/requirements.md#nfr-007), [SEC-008](../product/requirements.md#sec-008), [PRIV-003](../product/requirements.md#priv-003), [PRIV-005](../product/requirements.md#priv-005)
Related risks: [R-003](../risks/risk-register.md#r-003), [R-007](../risks/risk-register.md#r-007), [R-008](../risks/risk-register.md#r-008)
Related ADRs: [ADR-0006](0006-pre-sync-interchange.md), [ADR-0007](0007-backend-runtime-versions.md)
Evidence links: [ADR template](template.md), [ADR index](README.md), [Security/privacy baseline](../security/security-privacy-baseline.md), [Risk register](../risks/risk-register.md)

## Context

Optional synchronization would introduce accounts, sessions, object
authorization, deletion propagation, conflict handling, recovery, and
operational ownership. The local MVP has no account and must remain useful
without cloud access.

## Decision scope

This ADR covers identity, authentication, sessions, recovery, deletion, and
authorization assumptions for a future cloud service. It does not authorize
transmission or select a provider.

## Options considered

### Option A: Managed identity provider

May reduce identity implementation burden; introduces provider, availability,
privacy, and account-recovery dependencies.

### Option B: Project-managed standards-based identity

May offer more control; increases security, recovery, patching, and operating
responsibility.

### Option C: No account/synchronization

Preserves local privacy and scope; does not support cross-device sync.

## Evidence required

Define deployment topology, client types, threat model, identity/privacy
requirements, account recovery and deletion, standards/provider support,
object-authorization prototype, and operational owner. Test negative access
to every object operation.

## Decision

Proposed only. No authentication mechanism, provider, session lifetime, or
cloud data transfer is accepted.

## Consequences and tradeoffs

Cloud value must justify a new trust boundary and operational burden. The
The separately approved future local export/import path may be a lower-risk
alternative and must be considered before making sync a requirement.

## Security, privacy, accessibility, and operations

Review consent, minimization, authentication strength, session revocation,
cross-user authorization, deletion, audit data, recovery, rate limits, and
accessible account/error flows.

## Validation plan

WP-06 records the threat model, provider comparison, authorization tests,
recovery/deletion exercise, privacy review, and accepted decision.

## Rollback or revisit triggers

Revisit if authorization cannot be independently enforced, recovery/deletion
cannot be demonstrated, or operating cost/privacy impact exceeds the value
case.
