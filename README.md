# JobSkillRadar

Status: WP-01 documentation and governance baseline implemented; product
implementation has not started.

JobSkillRadar is planned as a local-first tool for capturing job
advertisements that a user is already viewing, storing them on the device,
and comparing evidence-backed qualifications across jobs. The MVP is
deliberately offline-capable and does not require an account, cloud service,
backend URL fetching, telemetry, or AI.

## Current repository state

On 2026-09-17, the repository was re-inspected at
C:\Projects\JobSkillRadar. Git metadata exists; the pre-WP-01 worktree was
clean on branch main at 7eace60. The repository had documentation only.
The WP-01 changes in this working tree are documentation and governance
artifacts and are intentionally not yet committed.

There is no extension, dashboard, API, package manifest, lockfile, CI
workflow, database schema, executable test suite, or installed project
dependency in this repository.

## Scope

The local MVP covers user-initiated capture, preview/edit, immutable original
evidence, local collections, deterministic Thai/English classification,
evidence snippets, correction overlays, comparison, export, deletion, and
security/accessibility/accuracy verification planning.

Cloud synchronization, AI assistance, backend services, mass crawling,
access-control circumvention, automatic job applications, file upload, and
PDF export are later or excluded scope. See the product brief for the
complete boundary.

## Documentation map

- Master plan: docs/plans/master-plan.md
- Product brief: docs/product/product-brief.md
- Requirements: docs/product/requirements.md
- Traceability: docs/product/traceability.md
- Glossary: docs/product/glossary.md
- Work-package roadmap: docs/roadmap/work-packages.md
- Engineering governance: docs/governance/engineering-governance.md
- Review guide: docs/governance/review-guide.md
- Risk method and register: docs/risks/method.md and docs/risks/risk-register.md
- ADR index: docs/adr/README.md
- Security and privacy baseline: docs/security/security-privacy-baseline.md
- Quality plans: docs/quality/test-strategy.md, including accessibility and accuracy
- WP-01 acceptance: docs/handoffs/wp-01-acceptance.md
- WP-02 planning handoff: docs/handoffs/wp-02-planning-handoff.md

All Markdown documentation is maintained as UTF-8 with LF line endings. A
document may be Proposed, Draft, Planned, Implemented, Tested, or Verified;
those labels are not interchangeable. No product control is claimed to be
implemented or verified by this README.
