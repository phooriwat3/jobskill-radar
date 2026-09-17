# Risk Method

Status: Draft - WP-01 source of truth  
Date: 2026-09-17  
Owner role: Project lead with security/privacy review

## Scope

The risk register covers product, data, security, privacy, accessibility,
accuracy, delivery, source-control, and future-cloud/AI risks. A risk is not
mitigated merely because it is documented.

## Scoring

Likelihood and impact are scored independently from 1 to 5. Inherent score
is likelihood multiplied by impact before planned treatment. Residual score
is recorded only after the stated verification evidence has been reviewed.

| Score | Likelihood meaning | Impact meaning |
|---|---|---|
| 1 | Rare; exceptional conditions required | Negligible; little user or delivery effect |
| 2 | Unlikely but plausible | Minor; limited reversible degradation |
| 3 | Possible in normal project conditions | Moderate; material rework, confusion, or bounded data/control failure |
| 4 | Likely without active control | Major; release failure, significant harm, or major rework |
| 5 | Almost certain or currently occurring | Severe; broad/irreversible harm, access-control failure, major data loss, or project invalidation |

| Score | Severity | Governance response |
|---|---|---|
| 1-4 | Low | Track and review at package boundary |
| 5-9 | Medium | Owner and action required; verify before affected release |
| 10-16 | High | Treatment and contingency required before affected implementation/release |
| 17-25 | Critical | Stop affected work/release until reduced or explicitly accepted by authorized owner |

## Control states

| State | Meaning |
|---|---|
| Planned | Described but not yet implemented or tested |
| Implemented | Exists in the product/process; execution evidence is not implied |
| Tested | A named test or check executed with recorded result |
| Verified | An accountable reviewer inspected the evidence and accepted it |

The register must never mark a control as Verified without evidence. A
planned control does not reduce the residual score.

## Workflow

1. Identify the cause, event, consequence, assets, requirements, and package.
2. Score inherent likelihood and impact; record the calculation.
3. Assign an accountable role and, before implementation, a named person.
4. Define treatment, action owner, due point, trigger, contingency, and
   verification method.
5. Review at planning, implementation, review, and package gates.
6. Score residual risk only after verification evidence exists.
7. Accept, transfer, avoid, reduce, or escalate the residual risk with the
   required authority.
8. Keep history when a risk is closed, superseded, or split.

## Required register fields

Each entry contains:

- ID, title, cause, event, consequence, category, affected assets and
  requirements.
- Owner role and named person when assigned.
- Raised/review dates and related package/ADR.
- Inherent likelihood, impact, score, and severity.
- Current controls with state.
- Treatment, action owner, due point, trigger, and contingency.
- Verification method and evidence link.
- Residual likelihood, impact, score, status, and accepting authority.

## Review cadence

- Critical: every active session and before any affected release.
- High: every package boundary and before affected implementation/release.
- Medium: at package boundary and when the trigger changes.
- Low: at least at the next package review.

The project lead records stale assumptions, changed triggers, and decisions
that move a risk to another package.
