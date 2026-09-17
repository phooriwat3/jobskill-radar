# JobSkillRadar

Status: WP-01 approved for documentation implementation; corrective amendment
recorded; independent re-review pending; product implementation has not
started.

JobSkillRadar is planned as a local-first tool for capturing job
advertisements that a user is already viewing, storing them on the device,
and comparing evidence-backed qualifications across jobs. The MVP is
deliberately offline-capable and does not require an account, cloud service,
backend URL fetching, telemetry, or AI.

## Current repository state

On 2026-09-17, the repository was re-inspected at
C:\Projects\JobSkillRadar. Git metadata exists. The original WP-01
implementation is committed as cd230e8, and the first corrective
documentation pass is recorded as 0a795b3. At the start of the authorized
second corrective amendment, branch main was at 0a795b3 and
`git status --short` returned no changes. The final verification
snapshot for that amendment recorded only documentation paths. These are
dated historical observations; later commits may change source-control
status.

There is no extension, dashboard, API, package manifest, lockfile, CI
workflow, database schema, executable test suite, or installed project
dependency in this repository.

## Scope

The local MVP covers user-initiated capture, preview/edit, immutable original
evidence, local collections, deterministic Thai/English classification,
evidence snippets, correction overlays, comparison, export, deletion, and
security/accessibility/accuracy verification planning. It supports export
only; import/interchange behavior and invalid-import testing remain deferred
unless separately approved.

Cloud synchronization, AI assistance, backend services, mass crawling,
access-control circumvention, automatic job applications, file upload, and
PDF export are later or excluded scope. See the product brief for the
complete boundary.

Analysis uses exactly the immutable job-text value accepted when the job is saved.
Evidence is represented by zero-based, end-exclusive UTF-8 byte offsets plus a
SHA-256 source digest of those exact bytes. Later metadata edits, including
URL/title changes, notes, collections, and corrections, are not analysis input.

## Documentation map

- [Approved WP-01 plan](docs/plans/wp-01-plan.md)
- [Master plan](docs/plans/master-plan.md)
- [Product brief](docs/product/product-brief.md)
- [Requirements](docs/product/requirements.md)
- [Traceability](docs/product/traceability.md)
- [Glossary](docs/product/glossary.md)
- [Work-package roadmap](docs/roadmap/work-packages.md)
- [Engineering governance](docs/governance/engineering-governance.md)
- [Review guide](docs/governance/review-guide.md)
- [Risk method](docs/risks/method.md) and [risk register](docs/risks/risk-register.md)
- [ADR index](docs/adr/README.md)
- [Security and privacy baseline](docs/security/security-privacy-baseline.md)
- [Quality plans](docs/quality/test-strategy.md), including accessibility and accuracy
- [WP-01 acceptance and corrective review handoff](docs/handoffs/wp-01-acceptance.md)
- [WP-02 planning handoff](docs/handoffs/wp-02-planning-handoff.md)

All Markdown documentation is maintained as UTF-8 with LF line endings. A
document may be Proposed, Draft, Planned, Implemented, Tested, or Verified;
those labels are not interchangeable. No product control is claimed to be
implemented or verified by this README.
