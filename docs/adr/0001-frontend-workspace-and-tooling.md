# ADR-0001: Frontend Workspace and Tooling

Status: Proposed
Date: 2026-09-17
Owners: Architecture owner, extension lead, dashboard lead
Deciders: Architecture owner and project lead; named individuals not assigned
Target package: WP-02
Related requirements: NFR-006, SEC-003, SEC-010
Related risks: R-002, R-013, R-014
Related ADRs: [ADR-0002](0002-local-dashboard-packaging.md), [ADR-0009](0009-accessibility-target-and-matrix.md), [ADR-0010](0010-naming-and-documentation-conventions.md)
Evidence links: [ADR template](template.md), [ADR index](README.md), [Requirements](../product/requirements.md), [Risk register](../risks/risk-register.md)

## Context

The MVP needs a browser extension, a local dashboard, shared deterministic
analysis contracts, tests, and reproducible builds. No package manifest or
tooling exists in the repository. The choice must support MV3 target
browsers, offline/local behavior, safe rendering, accessible UI, and a
maintainable dependency/update policy.

## Decision scope

This ADR covers frontend language, workspace/package layout, build, test, and
dependency tooling. It does not select the optional backend runtime or decide
dashboard packaging.

## Options considered

### Option A: Shared typed workspace

One typed language and workspace can share contracts and utilities between
extension and dashboard. It may reduce drift but can increase build/tooling
complexity and bundle-boundary risk.

### Option B: Separate extension and dashboard workspaces

Independent projects can use the simplest packaging for each surface, but
contract duplication and version drift become more likely.

### Option C: Minimal browser-native tooling

Fewer dependencies reduce supply-chain burden, but shared analysis, testing,
and reproducible builds may require more project-owned infrastructure later.

## Evidence required

Collect official support/release policy, MV3 and Chrome/Edge compatibility,
reproducible-build results, extension/dashboard sharing evidence, test
ecosystem fit, license/security/update burden, contributor environment
constraints, and a time-boxed compatibility spike. No production code is
authorized by this Proposed ADR.

## Decision

Proposed only. No frontend language, framework, workspace, or package tool is
accepted until the evidence is reviewed and the architecture owner approves
the selected option.

## Consequences and tradeoffs

Keeping the decision open prevents unsupported tooling from becoming an
accidental MVP dependency. It also blocks implementation readiness for
packages that need build details. The chosen option must preserve stable
contracts and allow later replacement without changing product requirements.

## Security, privacy, accessibility, and operations

Review must cover dependency provenance, secret handling, CSP and rendering
boundaries, permission packaging, keyboard/zoom/reflow support, lockfile
reproducibility, vulnerability/update ownership, and offline behavior.

## Validation plan

Record the spike commands, tool versions, browser matrix, build artifacts,
test results, license/security review, and independent review in WP-02
evidence. Link the accepted choice to updated requirements and risks.

## Rollback or revisit triggers

Revisit if a selected tool loses support, fails target-browser/CSP behavior,
introduces unacceptable dependency risk, prevents offline operation, or
cannot produce reproducible artifacts.
