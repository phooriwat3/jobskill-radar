# Engineering Governance

Status: Draft - WP-01 source of truth  
Date: 2026-09-17  
Applies to: planning, implementation, review, and handoff sessions

## Purpose and boundaries

This guide makes scope, evidence, ownership, and review state explicit. It
does not authorize product implementation by itself. A work package may
change only the files, behaviors, and evidence in its approved handoff.

WP-01 is documentation and governance only. It may update Markdown sources
and run read-only checks. It must not add application source, package
manifests, lockfiles, CI workflows, generated applications, databases,
infrastructure, or installed dependencies.

## Session protocol

| Session | Allowed work | Required output | Stop condition |
|---|---|---|---|
| Planning | Inspect repository, refine scope, identify evidence, propose decisions, risks, and acceptance | Approved plan and handoff | Stop before implementation |
| Implementation | Change only approved scope, record deviations, update tests/docs/risks within scope | Changed files, evidence log, residual risks, review handoff | Stop at approved boundary |
| Review | Independently inspect changed scope, run applicable checks, classify findings, and decide acceptance | Finding report with evidence and closure status | Do not silently fix implementation defects |

The same person may not be the sole planner, implementer, and reviewer for a
material decision unless the exception is recorded with a reason and
independent follow-up.

## State vocabulary

| State or label | Meaning | Required evidence |
|---|---|---|
| Proposed | An option or decision is under consideration; evidence or approval is incomplete | Context, alternatives, evidence needed, and owner |
| Draft | A source exists but has not completed its required review | Review status and open gaps |
| Approved | An authorized owner approved a plan or scope for the named package | Decision record and approver |
| In progress | Authorized implementation is underway | Active session and scoped change list |
| Blocked | Progress cannot continue until a named external decision or state change occurs | Blocker, owner, next action, and date |
| Implemented | The described change exists in the repository or product | File/change evidence |
| Tested | A named test or check executed with a recorded result | Command, environment, date, exit code, and output |
| Verified | An accountable reviewer inspected the relevant evidence and accepted it | Reviewer, date, evidence link, and decision |
| Accepted | A package or decision passed its required review and acceptance criteria | Acceptance record and unresolved-risk disposition |
| Rejected | An authorized decision or package was declined | Reason and follow-up |
| Superseded | A later decision replaces this one; history remains readable | Replacement link and effective date |
| Deprecated | Kept for history but no longer applicable | Scope and migration note |

Never use Verified as a synonym for planned or implemented. A clean command
exit code proves only that command's execution, not a product or security
claim.

## Definition of Ready

A work package is ready for implementation only when:

- Scope, non-goals, dependencies, owner roles, expected files, and acceptance
  criteria are approved.
- Requirement IDs and acceptance evidence are testable and traceable.
- Upstream contracts and ADRs are accepted, or a time-bounded spike is
  explicitly approved.
- Security, privacy, accessibility, accuracy, and operational implications
  have verification tasks.
- Test data is permitted and minimized, or a safe synthetic substitute is
  defined.
- Supported environment and tool assumptions are recorded.
- Every High/Critical risk has an owner, trigger, treatment, contingency, and
  verification method; risk acceptance names an authority.
- Unknowns that could invalidate implementation have an owner and due point.
- Repository state and unrelated changes have been inspected with available
  source control.

## Definition of Done

A work package is done only when:

- Every in-scope acceptance criterion has objective evidence.
- Applicable automated tests pass in the approved environment and manual
  checks have dated records and named reviewers.
- Applicable security, privacy, accessibility, accuracy, and operational
  checks are completed or marked not applicable with rationale.
- Requirements, documentation, ADRs, risks, limitations, schemas, and
  migration notes are current.
- No unresolved Critical or High review finding remains. A lower finding
  deferred to a later package has an owner and target.
- Dependency, generated-artifact, reproducibility, and license changes are
  reviewed.
- Independent review is complete or an approved exception records why and
  when it will be completed.
- The handoff lists changed files, commands, results, residual risks, open
  decisions, and rollback/recovery information where relevant.

For WP-01, done means the approved documentation set exists, IDs and links
are checked, decisions remain accurately labeled, role ownership is explicit,
and no feature code or infrastructure was introduced.

## Change control

1. Describe the requested change, reason, affected requirements, files,
   risks, and package boundary.
2. Classify it as clarification, correction, scope change, or emergency
   change.
3. Obtain approval from the package owner and any affected security, privacy,
   architecture, accessibility, or evaluation owner.
4. Update the source of truth, traceability, ADR/risk entries, and acceptance
   evidence in one coherent change.
5. Record rejected, deferred, and superseded decisions; do not rewrite
   accepted history without a replacement record.

Any scope change that introduces network transmission, accounts, cloud, AI,
backend URL fetching, or new sensitive data requires package reapproval.

## Documentation conventions

- Markdown is UTF-8 with LF line endings.
- Paths and IDs are stable; IDs are never reused for a different concept.
- Relative links point to repository files and headings where practical.
- Requirement IDs use FR, NFR, SEC, PRIV, A11Y, or ACC plus three digits.
- Risks use R plus three digits; ADRs use ADR plus four digits.
- Dates use ISO format YYYY-MM-DD.
- Claims distinguish planned, implemented, tested, and verified.
- Product, security, privacy, accessibility, and accuracy limitations are
  written next to the claim they qualify.
- No document claims legal compliance, malware protection, perfect
  extraction, or completed product testing without evidence.

## Accountable roles

The repository currently contains no named individuals. The following roles
are the minimum accountable placeholders and must be assigned to people before
implementation that requires their approval:

| Role | Accountability |
|---|---|
| Product owner | Scope, user value, release tradeoffs, acceptance |
| Project lead | Package coordination, repository/review process, handoffs |
| Architecture owner | Tooling, packaging, data contracts, technical decisions |
| Security owner | Threat boundaries, permissions, input/output security |
| Privacy owner | Data inventory, transmission, retention, deletion, corpus privacy |
| Extension lead | Capture flow, permissions, browser behavior |
| Dashboard lead | Local UI, comparison, correction, export, deletion |
| Analysis lead | Ontology, aliases, distinctions, deterministic analyzer |
| Evaluation lead | Corpus, annotation, metrics, uncertainty, accuracy gates |
| UX/accessibility owner | Accessibility target, manual matrix, user-facing semantics |
| Backend security owner | Future identity, object authorization, sync security |
| AI feature owner | Future provider boundary, consent, schema, fallback |

## Evidence record

Every acceptance or review record should state the command or artifact, tool
and version when relevant, date, environment, exit code or result, output
location, reviewer, and remaining limitations. A terminal result that is not
persisted must be described as session output rather than as a checked-in
report.
