# ADR-0009: Accessibility Target and Verification Matrix

Status: Proposed
Date: 2026-09-17
Owners: UX/accessibility owner, product owner, architecture owner
Deciders: Accessibility and product owners; named individuals not assigned
Target package: WP-02
Related requirements: A11Y-001 through A11Y-006
Related risks: R-010, R-013
Related ADRs: [ADR-0001](0001-frontend-workspace-and-tooling.md), [ADR-0002](0002-local-dashboard-packaging.md)
Evidence links: [ADR template](template.md), [ADR index](README.md), [Accessibility plan](../quality/accessibility-plan.md), [Risk register](../risks/risk-register.md)

## Context

The product must support keyboard use, logical focus, programmatic
semantics, contrast/target-size criteria, responsive/zoom behavior, and
Thai/English mixed text. The exact conformance target, browsers, assistive
technologies, and manual-review capacity are not yet evidenced.

## Decision scope

This ADR selects the evidence-backed conformance target and verification
matrix for the intended distribution. It does not claim legal compliance.

## Options considered

### Option A: A specific WCAG conformance target with a bounded matrix

Creates a testable release boundary; may require stakeholder and distribution
evidence before selection.

### Option B: Platform accessibility requirements without a formal target

Can start early but makes acceptance and coverage less reproducible.

### Option C: Targeted critical-workflow matrix only

Focuses effort on capture, evidence, correction, comparison, export, and
deletion; may under-cover the rest of the UI.

## Evidence required

Record distribution markets, applicable stakeholder or legal guidance,
target browsers, assistive technologies, automated tool support, manual-test
capacity, design-system feasibility, and representative bilingual content.

## Decision

Proposed only. WP-02 must recommend a specific target and matrix; WP-01
accepts no conformance level.

## Consequences and tradeoffs

An explicit target improves release clarity but creates testing obligations.
The matrix must include manual keyboard, focus, zoom, reflow, high-contrast,
and selected screen-reader checks in addition to automation.

## Security, privacy, accessibility, and operations

Review accessible error/status/evidence semantics, focus after capture/save/
delete, data minimization in assistive output, browser update policy, and
accessible recovery guidance.

## Validation plan

WP-02 publishes the target ADR decision, matrix, test data, automated rules,
manual scripts, reviewer roles, and exception/waiver process.

## Rollback or revisit triggers

Revisit when distribution browsers or assistive technologies change,
stakeholder needs show a coverage gap, or repeated failures indicate the
target/matrix is not usable.
