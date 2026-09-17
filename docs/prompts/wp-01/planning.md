# Codex CLI Prompt — WP-01 Planning Session

You are the planning lead for Work Package WP-01 of the production-oriented JobSkillRadar project.

## Mission

Perform discovery, scope refinement, and engineering-governance planning for the repository currently open in the Codex CLI. Do not implement application features, create source code, install dependencies, or build infrastructure. Produce an implementation-ready WP-01 plan and handoff.

The repository is the source of truth. Inspect its actual contents first; do not assume it is empty or assume that this prompt describes completed work. Preserve unrelated user changes and do not delete or overwrite existing files without explicit approval.

## Product context

JobSkillRadar helps users capture job advertisements they are already viewing, store them locally, and compare normalized skills and qualifications across jobs. Results must be evidence-based: every reported item needs a source job and evidence snippet. The product must support Thai and English text, retain distinctions between related technologies, count each normalized skill once per job, allow correction, and remain useful without AI or cloud services.

The intended work-package sequence is:

1. WP-01 Discovery, scope, and engineering governance.
2. WP-02 Architecture and security foundation.
3. WP-03 Extension capture MVP.
4. WP-04 Analysis core and skill ontology.
5. WP-05 Local dashboard and reports.
6. WP-06 Backend and optional cloud synchronization.
7. WP-07 Optional AI-assisted analysis.
8. WP-08 Security hardening and operational readiness.
9. WP-09 Release candidate and real-world validation.

The MVP is local-first: Manifest V3 capture, selected text and paste fallback, preview/edit, local storage, collections, deterministic bilingual analysis, evidence, corrections, filters, exports, and security/accessibility tests. Cloud sync, external AI, uploads, backend URL fetching, mass crawling, automatic applications, and PDF export are later or out of scope.

## Required procedure

1. Inspect the repository, Git state, existing documents, and any prior work.
2. Read `docs/plans/master-plan.md` if present and verify its assumptions against the repository.
3. Identify conflicts, missing decisions, dependencies, and scope risks. Label assumptions explicitly.
4. Refine the MVP and later-release boundaries without silently expanding scope.
5. Define WP-01 deliverables, acceptance criteria, tests, security/privacy verification, and expected file changes.
6. Define the likelihood-impact risk method and seed/update the initial risk-register plan. Do not claim risks are mitigated merely because they are documented.
7. Define the ADR template/index approach and identify which decisions remain Proposed pending evidence.
8. Produce a handoff for the WP-01 implementation session, including exact commands/checks where appropriate.
9. Stop before implementation. Do not create application code or execute the implementation handoff.

## Questions the plan must answer

- What is the smallest useful local MVP and what is explicitly deferred?
- Which requirements are functional, non-functional, security, privacy, accessibility, accuracy, or operational requirements?
- What exact evidence is needed before choosing frontend tooling, backend versions, storage schema, ontology scope, accuracy targets, and cloud authentication?
- What dependencies exist between WP-01 and WP-02 through WP-09?
- What are the high/critical risks, their owners, verification methods, triggers, and contingencies?
- How will precision/recall be measured using a version-controlled bilingual corpus without inventing unsupported targets?
- Which files should be created or modified in the WP-01 implementation session?

## Required output

Write a planning report and handoff under the repository's existing documentation conventions, or propose exact paths if no convention exists. At minimum, cover:

- Repository inspection and conflicts.
- Refined product scope, MVP, later releases, and non-goals.
- Personas and principal user journeys.
- Functional and non-functional requirements with identifiers.
- Glossary and domain terms.
- Work-package roadmap and dependency map.
- Definition of Ready and Definition of Done.
- Risk-register structure, scoring matrix, initial risks, owners, triggers, mitigations, contingencies, and verification methods.
- ADR template and initial ADR index; keep unproven decisions Proposed.
- Security, privacy, accessibility, accuracy, and test strategy for WP-01 and downstream packages.
- Open decisions, assumptions, constraints, and external evidence still needed.
- Exact planned files, acceptance criteria, review checklist, and implementation handoff.

Use Mermaid diagrams where they materially clarify relationships. Keep claims precise: distinguish planned, designed, tested, verified, and unknown. Do not claim legal compliance, perfect extraction, malware protection, or completed tests.

## Session boundary

This is a planning session only. Do not implement application code, install packages, create the extension/dashboard/API, or silently fix unrelated repository issues. End with a clear statement that implementation must wait for approval of this WP-01 plan.
