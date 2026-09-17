# Glossary and Domain Rules

Status: Draft - WP-01 source of truth
Date: 2026-09-17
Term owner role: Analysis lead; changes require product and privacy review

## Canonical terms

| Term | Definition and rule |
|---|---|
| Captured job | A user-created local record representing an advertisement and capture metadata. It is not proof that the source remains available or unchanged. |
| Capture | The deliberate user action and resulting proposed record before save. Capture is never background crawling. |
| Original evidence | The exact job text and metadata accepted at save time. It is immutable after creation except through explicit record deletion. |
| Analysis text | Exactly the immutable job-text value accepted when the job is saved. Page-derived relevant text, selected text, or manually pasted text becomes this value only after preview; source URL, page title, capture time, collection labels, user notes, later metadata edits, and corrections are never analysis input. |
| Edited capture | User-edited fields used for organization or display. Editing must not overwrite original evidence or silently replace analysis text. |
| Derived analysis | Analyzer output calculated only from analysis text and versioned configuration. It can be recomputed and is not source truth. |
| Correction | A separate, append-only or versioned user decision that accepts, rejects, adds, or remaps a derived result. |
| Evidence span | A zero-based, end-exclusive byte range into the exact UTF-8 bytes of the immutable saved analysis text, paired with its source digest and analyzer/ontology versions. It remains traceable to original evidence. |
| Evidence snippet | A bounded, safely rendered excerpt derived from an evidence span. It is explanatory, not independent source truth. |
| Source job | The captured-job record to which an analysis result is linked. |
| Canonical item | A stable ontology identifier used for aggregation, distinct from its display label and source aliases. |
| Alias | A surface form that may map to a canonical item under documented language and context rules. |
| Distinction rule | A rule preventing unsafe conflation of related terms, such as Java and JavaScript. |
| Qualification occurrence | One detected mention linked to a source span. Several occurrences may map to one canonical item. |
| Unique-per-job frequency | The number of distinct source jobs containing an accepted canonical item. Repeated mentions in one job count once. |
| Required/preferred signal | Evidence-backed classification of whether a qualification is mandatory or desirable. Unknown is valid. |
| Confidence | A rule-derived or calibrated uncertainty label with documented meaning. It is not a probability unless calibration is demonstrated. |
| Unknown | A deliberate result when evidence is insufficient to choose a stronger label or mapping. It must not be silently converted to a negative. |
| Collection | A user-defined grouping of captured jobs. |
| Duplicate candidate | A non-blocking similarity warning based on a documented key or score. It is not a guaranteed duplicate. |
| Local-only | Processing and storage performed on the device without a required account or transmission of captured content. |
| Ontology version | An identifier for a coherent set of canonical items, aliases, relationships, and distinction rules. |
| Analyzer version | An identifier for the deterministic rules and implementation used to derive analysis. |
| Corpus | A versioned set of permitted, minimized text samples and gold annotations used for evaluation. |
| Annotation split | A declared authoring, development, or hidden evaluation partition that prevents tuning against the final evaluation set. |
| Deterministic analysis | Analysis reproducible for fixed input, configuration, ontology, and analyzer versions without an external AI service. |
| Untrusted content | Page text, pasted text, separately approved future import data, source metadata, or future model output that must not be treated as executable instructions or privileged messages. |
| Permission budget | The minimum extension permissions and host access justified by documented user journeys. |
| UTF-8 byte offset | A zero-based, end-exclusive byte position in the UTF-8 encoding of the exact saved analysis text. No trimming, Unicode normalization, line-ending conversion, or locale-dependent transformation is applied before offset calculation. |
| Source digest | The SHA-256 digest of the exact UTF-8 bytes of the immutable saved analysis text used for an analysis result; it detects a mismatch before displaying or resolving an evidence span. |

## Domain rules

1. Original evidence is created once at save and is never rewritten by
   editing, analysis, or correction.
2. Analysis reads only the exact immutable job-text value accepted when the
   job is saved. URL, title, timestamps, collections, notes, later metadata edits, and
   corrections are not analysis input; only text accepted into that job-text
   value before save can be analyzed.
3. Analysis text is stored and hashed as exact UTF-8 bytes with SHA-256.
   Evidence offsets are zero-based, end-exclusive UTF-8 byte ranges and
   include the matching source digest.
4. Every reported qualification has a source job and at least one traceable
   evidence span or bounded snippet.
5. Aggregation uses canonical IDs and counts each accepted canonical item at
   most once per source job.
6. Corrections overlay or supersede derived results; they do not mutate
   original evidence or erase the analyzer version that produced the result.
7. Canonical IDs are stable and never reused for a different concept.
   Deprecated concepts remain resolvable through a migration or explicit
   remapping record.
8. Aliases require a language/context rule and must have tests for known
   distinction pairs and ambiguity cases.
9. Confidence labels must explain what uncertainty means. A confidence label
   must not be presented as a validated probability without evidence.
10. Unknown and low-confidence results remain visible and distinguishable from
   accepted results.
11. Source URLs are references only. No backend may fetch them or bypass a
   source access control.
12. Corpus text is not automatically product data: it requires permission,
    minimization, provenance, version, and deletion handling.
13. User-visible terminology changes require a glossary update, affected
    requirement/ADR links, and an impact review.

## Version and ownership rules

- The analysis lead owns canonical term definitions; the product owner
  approves user-facing category changes.
- The privacy owner reviews any new data field, corpus field, or transmission
  path.
- An ontology change increments its ontology version and records affected
  aliases, distinctions, fixtures, and evaluation slices.
- A breaking data or export change requires an ADR, migration note, and
  compatibility decision before implementation.
- A term may be deprecated, but its historical identifier and evidence links
  remain interpretable.
