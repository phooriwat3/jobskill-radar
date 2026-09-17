# Review Guide

Status: Draft - WP-01 source of truth  
Date: 2026-09-17

## Review principles

Review checks the approved scope, source-of-truth consistency, evidence,
security/privacy/accessibility/accuracy implications, and residual risk. The
reviewer should reproduce material checks and should not silently edit the
author's work.

Reviewers must distinguish:

- A documentation statement from an implementation claim.
- A command that ran from a product behavior that was verified.
- A planned control from an implemented or tested control.
- A known limitation from an accepted risk.

## Finding severity

| Severity | Definition | Required response |
|---|---|---|
| Critical | A credible path to severe data exposure, privilege misuse, destructive loss, unsafe release, or invalid package boundary | Stop affected work/release; owner and containment required |
| High | Material security, privacy, accessibility, accuracy, scope, or review failure likely to invalidate the affected release or package | Fix or formally accept before completion; contingency required |
| Medium | Important defect or missing evidence with bounded impact or workable mitigation | Owner and target package/date required |
| Low | Limited clarity, maintainability, or polish issue with no immediate release impact | Track and fix opportunistically |
| Informational | Observation, question, or improvement suggestion | Record if useful; no blocking effect |

Severity is about consequence in context, not effort. A repeated Medium
finding may be escalated if it indicates a systemic control failure.

## Independence

The reviewer should not be the sole author of the material being accepted.
For security, privacy, accessibility, accuracy, and authorization decisions,
the relevant accountable role should review or explicitly accept the
finding. If independence is unavailable, record the exception, reason,
reviewer, residual risk, and date for independent follow-up.

## Evidence standard

A finding or closure record should identify:

- Finding ID and severity.
- File, section, or requirement/ADR/risk ID.
- Observed fact and expected behavior or governance rule.
- Reproduction command, artifact, or review method.
- Impact and affected scope.
- Recommended treatment, owner, target, and contingency.
- Closure evidence, reviewer, date, and residual limitation.

Do not close a finding with a statement that the plan exists. Close it with
evidence that the required review or behavior occurred.

## Closure rules

- Critical and High findings must be closed, explicitly accepted by the
  authorized owner, or block completion.
- Medium findings may be deferred only with an owner, target package/date,
  trigger, and interim treatment.
- Low and Informational findings may be tracked without blocking.
- A finding is not closed because a document was edited; the changed
  evidence must be inspected.
- Superseded findings retain their history and link to the replacement.

## Finding format

Use this structure in a review record:

Finding ID: RV-YYYY-NNN  
Severity: Critical | High | Medium | Low | Informational  
Location: path, heading, requirement, ADR, or risk  
Observed: concise fact  
Expected: applicable rule or acceptance criterion  
Impact: user, security, privacy, accessibility, accuracy, delivery, or scope impact  
Treatment: action and contingency  
Owner: accountable role/person  
Target: package/date  
Status: Open | Accepted | Deferred | Closed  
Evidence: command/artifact/reviewer/date

## WP-01 review checklist

- Repository facts match the current inspection.
- Only section 17 files changed and no product implementation was introduced.
- Scope, exclusions, requirements, roadmap, and handoff agree.
- Every requirement and risk ID is unique and linked.
- Proposed ADRs do not present unsupported choices as accepted.
- Planned controls are not described as tested or verified.
- Encoding, line endings, links, diagrams, and terminology are consistent.
- Remaining High/Critical risks and independent-review status are visible.
