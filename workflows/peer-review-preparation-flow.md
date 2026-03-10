---
type: workflow
id: peer-review-preparation-flow
title: Peer Review Preparation Flow
description: "End-to-end manuscript preparation for peer review — from self-review through submission and revision"
tags: [Production, Tested]
connections:
  - target: manuscript-self-review
    type: uses
  - target: journal-fit-analysis
    type: uses
  - target: reviewer-response-crafting
    type: uses
  - target: manuscript-readiness-checker
    type: uses
  - target: journal-selector
    type: uses
  - target: self-critique-generator
    type: uses
  - target: cover-letter-writer
    type: uses
  - target: reviewer-response-drafter
    type: uses
  - target: claude-service
    type: runs_on
  - target: journal-submission-standards
    type: references
  - target: peer-review-survival-guide
    type: references
  - target: reviewer-response-template
    type: uses
metadata:
  estimated_duration: "60-90 minutes"
  trigger: manual
---

## Overview

This workflow guides researchers through the complete peer review lifecycle: preparing a manuscript for initial submission, selecting an appropriate journal, writing a cover letter, and — after review — crafting responses to reviewer comments for revision. The flow is designed to be used at two distinct points in the publication timeline: pre-submission (Stages 1-4) and post-review (Stage 5).

## Pipeline Stages

### Stage 1: Manuscript Readiness Check

**Input:** Complete manuscript draft, target journal guidelines (if known)

Invoke the **manuscript-self-review** skill via the **manuscript-readiness-checker** prompt. Evaluate the manuscript against a comprehensive set of submission criteria covering structure, formatting, content completeness, and common rejection triggers.

**Output:** Readiness report with a pass/fail assessment for each criterion, specific issues to address, and an overall readiness score.

**Checkpoint:** If the readiness score is below 70%, address the identified issues before proceeding. Focus on critical failures (missing sections, incomplete methods, unsupported conclusions) first, then moderate issues (formatting, word count, figure quality).

### Stage 2: Journal Selection

**Input:** Manuscript abstract, keywords, methodology type, field of study, author preferences (impact factor range, open access requirements, turnaround time expectations)

Invoke the **journal-fit-analysis** skill via the **journal-selector** prompt. Analyse the manuscript's fit with potential target journals and produce a ranked recommendation list.

**Output:** Ranked list of 5-8 recommended journals with fit scores, key decision factors, and potential concerns for each.

**Checkpoint:** Review the recommendations against your own knowledge of the field. Consider factors the AI may not fully capture: editorial board relationships, recent special issues, known publication bottlenecks, or political considerations within your sub-field.

### Stage 3: Self-Critique

**Input:** Complete manuscript, target journal scope and requirements, relevant reviewer criteria for the field

Invoke the **manuscript-self-review** skill via the **self-critique-generator** prompt. Produce a rigorous self-critique that anticipates likely reviewer objections, identifies methodological weaknesses, and flags areas where the argument could be strengthened.

**Output:** Detailed self-critique with prioritised recommendations for strengthening the manuscript before submission.

**Checkpoint:** Address all critical and major issues identified in the self-critique. For minor issues, make a deliberate decision to address or accept each one. Document your rationale for any issues you choose not to address — this will help when responding to reviewers later.

### Stage 4: Cover Letter

**Input:** Manuscript title, abstract, key findings, target journal name and editor, statement of novelty

Invoke the **reviewer-response-crafting** skill via the **cover-letter-writer** prompt. Draft a professional cover letter tailored to the selected journal.

**Output:** Complete cover letter ready for submission.

**Checkpoint:** Review the cover letter for accuracy (correct editor name, correct journal name, accurate representation of findings). Ensure it highlights what makes this manuscript a good fit for this specific journal, not just a generic summary.

### Stage 5: Reviewer Response (Post-Review)

**Input:** Reviewer comments (all reviewers), editor's decision letter, original manuscript, revised manuscript

Invoke the **reviewer-response-crafting** skill via the **reviewer-response-drafter** prompt. Draft point-by-point responses to every reviewer comment using the **reviewer-response-template** asset.

**Output:** Complete response document addressing every reviewer comment with specific references to changes made in the revised manuscript.

**Checkpoint:** Verify that every reviewer comment has been addressed — even minor ones. Ensure the tone is respectful and professional throughout, even for comments you disagree with. Cross-check that all claimed changes are actually present in the revised manuscript.

## Error Handling

- If the manuscript readiness check identifies structural problems (missing abstract, incomplete methods), halt the pipeline and address these before proceeding to journal selection
- If no suitable journals are found (all fit scores below 50%), consider whether the manuscript needs repositioning: a different framing, additional analyses, or a shift in target audience
- If the self-critique identifies a fatal flaw (e.g., fundamental methodological error, insufficient sample size for the claimed conclusions), escalate this to the researcher rather than proceeding to submission
- If reviewer comments are contradictory (Reviewer 1 wants more detail, Reviewer 2 wants less), address both comments explicitly, explain the contradiction to the editor, and state your resolution rationale
- If the editor requests a major revision but the reviewers' comments suggest rejection, address all comments thoroughly but consider whether a different journal might be a better fit for a substantially revised version
