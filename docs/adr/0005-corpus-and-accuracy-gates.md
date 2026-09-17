# ADR-0005: Corpus and Accuracy Gates

Status: Proposed
Date: 2026-09-17
Owners: Evaluation lead, analysis lead, privacy owner
Deciders: Evaluation and product owners; named individuals not assigned
Target package: WP-04
Related requirements: ACC-001 through ACC-008, PRIV-006, PRIV-007
Related risks: R-004, R-005, R-014
Related ADRs: [ADR-0004](0004-bilingual-ontology-governance.md)
Evidence links: [ADR template](template.md), [ADR index](README.md), [Accuracy plan](../quality/accuracy-evaluation-plan.md), [Security/privacy baseline](../security/security-privacy-baseline.md)

## Context

Accuracy claims require a permitted, minimized, versioned bilingual corpus,
annotation rules, leakage-resistant splits, and separate scoring for entity
mapping, evidence spans, and required/preferred classification. WP-01 must
not invent target percentages before baseline measurement.

## Decision scope

This ADR covers corpus governance, annotation, split policy, metrics,
uncertainty, and release-gate approval. It does not create corpus data or set
unsupported thresholds.

## Options considered

### Option A: Real-world permitted corpus

More representative of user input; permission, minimization, and retention
work are required.

### Option B: Synthetic and adversarial corpus

Useful for edge cases and safe sharing; it cannot alone establish real-world
representativeness.

### Option C: Mixed corpus with declared slices

Can combine representative and edge-case coverage; reports must prevent
aggregate metrics from hiding slice failures.

## Evidence required

Approve provenance and permission policy, annotation guide, double-annotation
trial, adjudication process, split manifest, exact/overlap scoring rule,
baseline metrics, support counts, uncertainty method, and user-harm analysis.

## Decision

Proposed only. The baseline-first sequence is required, but no numeric target
or release gate is accepted in WP-01.

## Consequences and tradeoffs

Reporting slices and uncertainty may delay broad claims, but it makes missing
coverage and harmful false positives visible. Synthetic results must be
reported separately from permitted representative results.

## Security, privacy, accessibility, and operations

Review personal data, licensing/provenance, corpus access, deletion,
annotation tooling, mixed-language display, reproducible runs, and artifact
retention.

## Validation plan

WP-04 publishes a version manifest, annotation/agreement record, frozen split,
baseline report, error analysis, and approved target decision.

## Rollback or revisit triggers

Revisit if provenance is withdrawn, leakage is found, support is too sparse,
annotation agreement is unstable, or target gates reward unsafe false
positives/negatives.
