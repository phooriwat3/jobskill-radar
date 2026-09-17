# Accuracy Evaluation Plan

Status: Proposed - baseline and targets not yet available
Date: 2026-09-17
Owners: Evaluation lead and analysis lead; named individuals not assigned

This plan defines how to measure deterministic analysis. It does not claim
accuracy, representative coverage, or a release threshold.

## Evaluation objects

The evaluation version must bind:

- Corpus version and provenance register.
- Text fixture and permitted-use status.
- Annotation-guide version.
- Ontology version.
- Analyzer/rule version.
- Scoring specification.
- Split manifest.
- Evaluation output and error analysis.

## Analysis input and evidence offsets

The analyzer input is exactly the saved original-evidence job-text field.
That field may come from relevant page-derived text, selected text, or manual
paste after preview. Source URL, page title, capture time, collection labels,
user notes, later edits, and correction text are excluded unless deliberately
copied into job text before save.

The analyzer consumes the exact UTF-8 byte sequence of that field. It must not
trim, normalize Unicode, convert line endings, or apply locale-dependent
transforms before calculating offsets. Each predicted span is a zero-based,
end-exclusive UTF-8 byte range plus a digest of the exact analysis text.
Evaluation fixtures must verify that the same input bytes, analyzer version,
ontology version, and configuration reproduce the same spans and digest.

## Corpus governance

Sampling is defined before target setting. Record language slice (Thai,
English, mixed), job family, seniority, source format, length, and presence or
absence of each qualification category. Synthetic/adversarial samples are
useful for edge cases but must be reported separately from permitted
representative samples.

Raw third-party advertisements must not enter the repository until
permission/retention is approved. Minimize names, contact details, tracking
parameters, unrelated page text, credentials, and other unnecessary
sensitive data. Opaque sample IDs should separate metadata from text where
practical.

The corpus register records provenance or synthetic-generation method,
permission, minimization review, annotators, adjudicator, split, version,
removal path, and limitations.

## Annotation protocol

The annotation guide must specify:

- Annotation unit and the documented UTF-8 byte-offset/digest convention.
- Canonical item, source span, category, required/preferred/unknown label,
  and language.
- Aliases, negation, headings, lists, experience ranges, implicit signals,
  ambiguous terms, and overlapping spans.
- When to choose unknown, request adjudication, or decline a mapping.
- Distinction rules and ontology-version compatibility.
- Independent double annotation for a declared sample and adjudication by a
  named domain reviewer.

Agreement is reported before adjudication changes the gold label. Disputed
cases remain visible in the error analysis.

## Splits and leakage control

Use a declared authoring/development/hidden evaluation split, or an equivalent
split suitable for the corpus. Do not tune analyzer rules, aliases, or
thresholds directly against the final evaluation set. Record duplicate,
near-duplicate, source, and template leakage checks. Freeze the evaluation
split and scoring rules before the reported run.

## Metrics

For each class and slice, report TP, FP, FN, support, precision, recall, and
F1. Where denominators are defined:

- Precision = TP / (TP + FP)
- Recall = TP / (TP + FN)
- F1 = 2 x precision x recall / (precision + recall)

Define zero-denominator handling before scoring. Report micro and macro
aggregation and error categories. Score separately:

1. Entity/category recognition and canonical mapping.
2. Evidence-span correctness, using a declared exact or overlap rule.
3. Required/preferred/unknown classification.
4. Unique-per-job frequency behavior for repeated mentions and aliases.

Report language, category, job family, seniority, source-format, length,
synthetic/representative, and ambiguity slices where support permits.

## Support and uncertainty

Every metric includes raw support counts. Small or missing slices must be
visible rather than hidden in an aggregate. Use an approved uncertainty
method, such as confidence intervals or a documented resampling procedure,
when sample support makes point estimates misleading. The method and
assumptions belong in the evaluation output.

## Baseline-first target setting

No percentage target is invented in WP-01. The sequence is:

1. Approve corpus inclusion, provenance, minimization, and annotation rules.
2. Run an annotation trial, measure agreement, and adjudicate systematic
   ambiguity.
3. Freeze a corpus version, split manifest, ontology version, and scoring rule.
4. Run a deterministic baseline and publish slice metrics, support, and error
   analysis.
5. Assess false-positive and false-negative harm by category and user journey.
6. Propose release gates with stakeholder rationale, minimum support,
   uncertainty, and regression tolerance.
7. Accept targets in an ADR; change them only with a new rationale and
   compatible corpus/evaluation version.

## Evaluation evidence record

Each run records command/tool version, date, input versions, configuration,
output location, reviewer, failures, exclusions, uncertainty, limitations,
and whether the result is exploratory, baseline, regression, or release
evidence. A metric run is not automatically a verified release gate.
