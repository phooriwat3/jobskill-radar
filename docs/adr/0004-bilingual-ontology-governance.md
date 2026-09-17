# ADR-0004: Bilingual Ontology Governance

Status: Proposed
Date: 2026-09-17
Owners: Analysis lead, evaluation lead, privacy owner
Deciders: Analysis and product owners; named individuals not assigned
Target package: WP-04
Related requirements: FR-007, FR-009, FR-010, ACC-001, ACC-004, ACC-006, PRIV-006
Related risks: R-004, R-005, R-014
Related ADRs: [ADR-0003](0003-local-data-model-and-migrations.md), [ADR-0005](0005-corpus-and-accuracy-gates.md)
Evidence links: [ADR template](template.md), [ADR index](README.md), [Glossary](../product/glossary.md), [Accuracy plan](../quality/accuracy-evaluation-plan.md)

## Context

The analyzer must support Thai and English qualification wording, aliases,
meaningful distinctions, required/preferred signals, evidence spans, and
unique-per-job counts. The repository has no ontology or corpus yet. A
canonical ID must remain stable while terminology evolves.

## Decision scope

This ADR covers ontology representation, categories, aliases, distinctions,
identifier ownership, deprecation, version compatibility, and review. It
does not set accuracy percentages or implement analyzer rules.

## Options considered

### Option A: Flat canonical vocabulary with governed aliases

Simple aggregation and stable IDs; context-sensitive distinctions may need
explicit rule layers.

### Option B: Hierarchical concept graph

Can model relationships and related technologies; may create ambiguous
aggregation and higher governance cost.

### Option C: Hybrid canonical items plus explicit relations

Preserves stable aggregation while recording relationships; requires clear
relation semantics and more fixtures.

## Evidence required

Collect representative Thai/English samples, ambiguity and confusion-pair
analysis, domain-review capacity, user journeys, versioning needs, and
license/provenance constraints. Run annotation and ontology review before
acceptance.

## Decision

Proposed only. No initial coverage, alias set, relation model, or distinction
set is accepted by WP-01.

## Consequences and tradeoffs

Stable IDs and visible uncertainty are more important than broad early
coverage. Narrower supported claims may be necessary while evidence is
limited. Ontology changes must be versioned and evaluated for regressions.

## Security, privacy, accessibility, and operations

Review corpus minimization, source provenance, user correction semantics,
mixed-script display, long labels, and safe evidence rendering. Avoid
encoding a canonical item as a user or employer score.

## Validation plan

WP-04 records the ontology version, alias/distinction fixtures, review
outcomes, slice metrics, and migration/remapping notes.

## Rollback or revisit triggers

Revisit if confusion pairs remain harmful, language slices are unsupported,
IDs cannot be migrated, or user corrections reveal an unsafe distinction.
