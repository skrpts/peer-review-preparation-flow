# Release Notes

## v1.1.34
GH#863 Wave 1 — fix K-045 intent/output-mismatch: wire the two deliverable-producing prompts that were never invoked. `self-critique-generator` (the self-critique) and `cover-letter-writer` (the submission cover letter, the primary deliverable) now run as execution steps in dependency order, with the cover letter as the final content step before language polish. Adds two backing skills (`self-critique-analysis`, `cover-letter-drafting`) so the new `from_step` targets resolve by title; converts the wired prompts' cross-step refs to named context_params with `bindings:`; re-pins `polish-language` to 1.0.6 and binds its `source` slot to the cover letter. Skills 3→5, total 12→14.

## v1.1.33
GH#845 — republish with American English (en-US) content, completing the source-only GH#805 flip that never reached the Hub. Copy only — no functional or behaviour change.

## v1.1.32
GH#745 — declare per-step `output: {name, type}` on every execution step (journal_recommendations/text, research_gaps/text, reviewer_response/text, response_template/text, readiness_assessment/text, polished_manuscript/text, methodology_assessment/text, compliance_verdict/decision). Lights up the #744 rich flow-map with named, typed outputs. Content-only; no bindings or logic changes.

## v1.1.31
GH#645 Row 3b — migrate to K-037 dep-referenced schema. Strip 10 inline shared-content files and declare 10 hub-shared deps (UUID id + slug name + version + checksum from `gen-dep-checksums.mjs`). Closes pre-Step-3 inline-vendoring for this bundle.

## v1.1.30
Wave 2: re-signed with canonical engine signing pipeline.

## v1.1.29
Tags migrated inline into manifest (GH#586). tags.yaml retired.

## v1.1.28
Bundle re-signed with canonical engine signing pipeline (Wave 2 migration).

## v1.1.27
Signature fix — RELEASE_NOTES.md now included in integrity checksum.

## v1.1.26
Initial catalog release with full structural and content-quality validation. All scanner checks pass.
