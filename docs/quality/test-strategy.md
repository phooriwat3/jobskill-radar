# Test Strategy

Status: Planned - WP-01 documentation and downstream verification strategy
Date: 2026-09-17
Owner role: Project lead with package owners; named individuals not assigned

WP-01 verifies documentation and governance quality. It does not create a
product test suite or claim product behavior.

## Test layers

| Layer | Planned scope | Primary packages |
|---|---|---|
| Unit | Normalization, aliases, distinctions, required/preferred rules, URL/schema validation, unique-per-job aggregation, export escaping | WP-03/WP-04/WP-05 |
| Property/fuzz | Unicode and mixed-language text, malformed messages, large inputs, UTF-8 byte offsets, deterministic/idempotent behavior | WP-03/WP-04/WP-05 |
| Contract | Extension messages, local schema/migrations, analyzer output, MVP exports, future approved import schemas, and future API schemas | WP-02/WP-03/WP-04/WP-05/WP-06 |
| Integration | Capture-to-store, store-to-analysis, correction overlay, deletion, migration, sync authorization/conflicts | WP-03 through WP-07 |
| End-to-end | Offline capture, preview/save, analyze, correct, compare, export, and delete | WP-03/WP-05 |
| Security | Hostile markup, script-like text, unsafe URLs, sender confusion, message size, CSP assumptions, dependencies, multi-user authorization | WP-02/WP-03/WP-06/WP-08 |
| Accessibility | Automated rules plus keyboard, focus, zoom/reflow, high contrast, and selected screen-reader checks | WP-02/WP-05/WP-09 |
| Accuracy | Frozen bilingual corpus, slice metrics, evidence-span/classification metrics, regression/error reports | WP-04/WP-09 |
| Operational | Reproducible build, upgrade/rollback, backup/restore where cloud exists, dependency update, incident/recovery exercises | WP-02/WP-06/WP-08 |

## Critical behavior coverage

| Behavior | Required evidence |
|---|---|
| Explicit capture and fallback | Permission review, page/selection/paste fixtures, manual workflow |
| Preview and edit | Before-save inspection and safe rendering |
| Original evidence | Immutability test and separate derived/correction records |
| Determinism | Same input/configuration/version produces stable serialized output |
| Bilingual analysis | Language/category slices, aliases, distinctions, unknown handling |
| Unique-per-job count | Repeated mentions and alias fixtures count once |
| Evidence | Every result links to source job, exact analysis-text digest, and bounded UTF-8 byte span/snippet |
| Correction | Accept/reject/add/remap overlay leaves evidence unchanged |
| Comparison/filter | Accessible selection and unique-frequency behavior |
| Export only | Versioned JSON/CSV schema, bounded fields, safe CSV, and round-trip behavior; import only if separately approved |
| Deletion | Job, collection, derived data, corrections, and all-data paths |
| Offline | Network unavailable after installation does not block MVP journeys |

## Test-data governance

Use permitted and minimized corpus data for accuracy. Use synthetic hostile
fixtures for scripts, unsafe URLs, oversized messages, formula-like CSV
cells, malformed messages, Unicode edge cases, UTF-8 byte-offset stability,
and permission/message confusion. Do not commit real advertisements or
personal data without the corpus governance decision. Import fixtures are
deferred unless separately approved.

## Failure and recovery

Tests must show that previously committed local records survive validation,
analysis, export, migration, and deletion failures as applicable. Error
messages are actionable but non-sensitive. Recovery fixtures must record
which data is restored, which is intentionally not restored, and how version
compatibility is handled.

## Accessibility and security integration

Security and accessibility checks are release evidence, not optional polish.
Each package maps its changed requirements to the security/privacy baseline,
accessibility plan, risk register, and review guide. A passing automated tool
does not close a manual or design-boundary risk.

## WP-01 documentation checks

The approved WP-01 plan calls for:

- Repository file inventory and Git status.
- Stale-term/status scan.
- Requirement-ID scan.
- ADR heading/status/decision scan.
- Risk-ID/severity/control-state scan.
- Link, Markdown, duplicate-ID, required-section, Mermaid, terminology,
  encoding, and diff-whitespace checks where tools are available.

WP-01 may run read-only commands or ephemeral checks. It must not install a
linter, create configuration, or add executable test/build scripts. The
acceptance report records command, tool/version, date, exit code, output
location, and limitations for each check.

## Result language

Each result is recorded as passed, failed, not run, or not applicable with a
reason. Tested means the command or test executed. Verified means the
accountable reviewer accepted the evidence. Planned controls are not tests.
