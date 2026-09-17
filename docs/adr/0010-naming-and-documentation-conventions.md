# ADR-0010: Naming and Documentation Conventions

Status: Proposed
Date: 2026-09-17
Owners: Project lead, product owner
Deciders: Product/project owners; named individuals not assigned
Target package: WP-01
Related requirements: PRIV-005, ACC-001, ACC-008
Related risks: R-009, R-013, R-014
Related ADRs: [ADR-0001](0001-frontend-workspace-and-tooling.md)
Evidence links: [ADR template](template.md), [ADR index](README.md), [Engineering governance](../governance/engineering-governance.md), [Master plan](../plans/master-plan.md)

## Context

The working directory is C:\Projects\JobSkillRadar and the product name is
JobSkillRadar. Existing planning text also uses jobskill-radar as a proposed
slug. The repository has docs/plans and docs/prompts conventions, while the
WP-01 implementation establishes the broader documentation map. The
canonical public name and slug have not been approved.

## Decision scope

This ADR covers product/repository naming, path conventions, document
identifiers, status vocabulary, encoding, line endings, and source-of-truth
ownership. It does not rename the working directory or remote.

## Options considered

### Option A: JobSkillRadar product with jobskill-radar slug

Readable product branding and a conventional repository slug; availability
and sponsor approval remain to be checked.

### Option B: Use the existing workspace spelling as the canonical slug

Avoids migration; may not fit hosting/package conventions or sponsor naming.

### Option C: New sponsor-approved name

May improve ownership and availability; creates migration cost and ambiguity
until approved.

## Evidence required

Obtain sponsor naming decision, hosting/VCS constraints, package/domain
availability where relevant, migration cost, and approval of UTF-8/LF
documentation conventions. Keep the current path stable until a decision is
accepted.

## Decision

Proposed only. The current working convention is a temporary baseline:
JobSkillRadar for product text, jobskill-radar as a proposed slug, stable
relative Markdown paths, UTF-8, LF, and numbered IDs. No public rename or
remote change is authorized.

## Consequences and tradeoffs

The temporary convention allows documentation to proceed while preserving a
low-cost migration point. A later accepted name change must update links,
package paths, metadata, and user-facing references through a migration
record.

## Security, privacy, accessibility, and operations

Consistent names reduce misrouting of data and decisions. Documentation
encoding and line-ending consistency supports review and reproducibility; it
does not prove product security or legal compliance.

## Validation plan

Record the sponsor decision, VCS/hosting check, availability result,
encoding/line-ending check, link update plan, and independent review.

## Rollback or revisit triggers

Revisit when sponsor or hosting constraints change, the proposed slug is
unavailable, or migration cost is lower before implementation begins.
