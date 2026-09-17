# Accessibility Plan

Status: Proposed - target not selected
Date: 2026-09-17
Owner role: UX/accessibility owner; named individual not assigned

WP-01 defines the selection and evidence process. It does not claim a WCAG
conformance level or that any UI is accessible.

## Scope

Accessibility applies to capture, preview/edit, save/error states, evidence
inspection, confidence and correction controls, collections, filtering,
comparison, export, deletion, and any future account or AI consent flow.

The plan includes Thai, English, mixed-language content, long tokens, source
snippets, uncertainty, hostile-looking text, responsive layouts, and browser
zoom.

## Required journeys

### Manual fallback journey

When automatic extraction is empty or incomplete, the user reaches the
selection or paste fallback with keyboard navigation, supplies the intended
job text, reviews the preview, and receives a clear non-sensitive status if
capture fails. The fallback must remain usable without relying on a page
adapter or network request.

### Accessible evidence and deletion journey

A keyboard-only or assistive-technology user invokes capture, reviews the
preview, moves through evidence snippets and confidence/correction states,
compares jobs, exports data, and deletes a job or all local data. Focus,
names, status changes, errors, Thai/English text, long tokens, zoom, and
reflow are checked at each step. Color alone must not communicate a decision.

## Target selection

WP-02 must recommend a specific evidence-backed target before UI
implementation is accepted. The decision must consider:

1. Intended distribution markets and supported browsers.
2. Stakeholder needs and applicable guidance; this is not a legal-compliance
   claim.
3. Browser/assistive-technology support and test capacity.
4. Design-system/component feasibility.
5. Core workflow risk and available manual review.

The selected target, exceptions, matrix, and approval belong in ADR-0009.

## Verification matrix

The exact browser and assistive-technology versions are TBD until distribution
and support evidence exist. The matrix must include at least:

| Area | Automated evidence | Manual evidence | Core scenarios |
|---|---|---|---|
| Keyboard/focus | Semantic/focus rule checks | Tab order, visible focus, no trap, focus restoration | Capture, preview, correction, export, delete |
| Names/semantics | Accessibility tree and label checks | Screen-reader announcement and state changes | Evidence, confidence, errors, duplicate warning |
| Contrast/target size | Approved rule set after target selection | High-contrast and non-color interpretation | Status, required/preferred, correction state |
| Zoom/reflow | Layout rule checks where available | Agreed viewport and browser zoom levels | Dashboard filters, evidence, comparison, export |
| Mixed language | Character/overflow fixtures | Thai/English reading, long tokens, wrapping | Capture preview, snippets, canonical labels |
| Errors/recovery | Required-field and error association checks | Actionable, non-sensitive recovery messages | Storage failure, deletion; import errors only after separate approval |
| Future consent | Label/state checks | Purpose-specific opt-in and denial path | Sync/AI consent if approved |

## Manual review protocol

For each target combination, record:

- Browser, operating system, assistive technology, and version.
- Build/revision and test data identifier.
- Workflow and step.
- Expected semantics and observed result.
- Screenshot or artifact location when safe.
- Finding severity, owner, and closure evidence.

Reviewers must test keyboard-only operation, focus order/visibility,
browser zoom, reflow, high-contrast or equivalent settings, text resizing,
and selected screen-reader journeys. Color must not be the sole carrier of
required/preferred, confidence, error, or correction state.

## Release gate

Before a release claims the selected target, all critical workflows must have
automated and manual evidence, unresolved Critical/High accessibility
findings must be closed or authorized to block release, and limitations must
be disclosed. A missing manual test is not evidence of success.

## Open evidence

- Distribution and browser support decision.
- Specific target and success criteria.
- Assistive-technology matrix and manual-review capacity.
- Representative Thai/English and long-token fixtures.
- Accessible component and error-message standards.
- Named reviewer and escalation/waiver authority.
