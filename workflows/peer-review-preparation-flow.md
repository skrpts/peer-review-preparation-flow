---
type: workflow
id: peer-review-preparation-flow
title: Peer Review Preparation Flow
description: "End-to-end manuscript preparation for peer review — from self-review through submission and revision"
tags: [Production, Tested, Academic, Learning, Review]
connections:
  - target: manuscript-self-review
    type: uses
  - target: journal-fit-analysis
    type: uses
  - target: reviewer-response-crafting
    type: uses
  - target: methodology-assessment
    type: uses
  - target: llm-service
    type: runs_on
  - target: journal-submission-standards
    type: references
  - target: peer-review-survival-guide
    type: references
  - target: reviewer-response-template
    type: uses
  - target: brief-compliance-check
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

Invoke the **manuscript-self-review** skill via the **manuscript-readiness-checker** prompt. Evaluate the manuscript against a thorough set of submission criteria covering structure, formatting, content completeness, and common rejection triggers.

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

## Inputs

| Name | Required | Description | Example |
|------|----------|-------------|---------|
| `{{input.complete_manuscript_draft}}` | Yes | Complete manuscript draft | `Paste your full manuscript text here.` |
| `{{input.target_journal_guidelines}}` | Yes | Target journal name and guidelines | `Nature Communications — see author guidelines at...` |
| `{{input.manuscript_abstract}}` | Yes | Manuscript abstract | `Paste your manuscript abstract here.` |
| `{{input.keywords}}` | No | Keywords describing the manuscript | `growth, onboarding, retention` |
| `{{input.discipline}}` | No | Academic discipline | `Psychology` |
| `{{input.study_type}}` | No | Type of study | `Randomised controlled trial` |
| `{{input.methodology}}` | No | Methodology used in the study | `Mixed methods — survey and interviews` |
| `{{input.author_preferences}}` | No | Preferences for journal selection | `Impact factor 3+, open access preferred, turnaround under 3 months` |
| `{{input.excluded_journals}}` | No | Journals to exclude from recommendations | `Journal of X (previously rejected)` |
| `{{input.manuscript_title}}` | No | Title of the manuscript | `The Impact of X on Y: A Mixed-Methods Study` |
| `{{input.authors}}` | No | Author names | `Smith, J., Jones, A., and Brown, K.` |
| `{{input.editor_name}}` | No | Name of the target journal editor | `Professor Jane Smith` |
| `{{input.key_findings}}` | No | Key findings from the study | `Intervention X reduced Y by 30% (p < .001)` |
| `{{input.novelty_statement}}` | No | What is novel about this work | `First study to examine X in the context of Y` |
| `{{input.ethical_approval}}` | No | Ethical approval details | `Approved by University of X Ethics Committee, ref: 2025-123` |
| `{{input.conflicts_of_interest}}` | No | Conflicts of interest declaration | `None declared` |
| `{{input.ai_disclosure}}` | No | AI tool usage disclosure | `Claude was used for literature search assistance` |
| `{{input.reviewer_comments}}` | No | Reviewer comments (for Stage 5 — post-review) | `Paste all reviewer comments here` |
| `{{input.editor_letter}}` | No | Editor decision letter (for Stage 5) | `Paste the editor decision letter here` |
| `{{input.revised_manuscript}}` | No | Revised manuscript (for Stage 5) | `Paste the revised manuscript here` |
| `{{input.changes_list}}` | No | List of changes made in revision (for Stage 5) | `Added sample size justification, revised discussion` |

## Outputs

| Name | Description |
|------|-------------|
| Readiness report | Readiness report with a pass/fail assessment for each criterion, specific issues to address, and an overall readiness score |
| Ranked list of 5-8 recommended journals | Ranked list of 5-8 recommended journals with fit scores, key decision factors, and potential concerns for each |
| Detailed self-critique | Detailed self-critique with prioritised recommendations for strengthening the manuscript before submission |
| Complete cover letter ready for submission | Complete cover letter ready for submission |
| Complete response document addressing every reviewer comment | Complete response document addressing every reviewer comment with specific references to changes made in the revised manuscript |

## Setup

Before running this workflow:

1. No external services required — paste your content directly and provide any supporting context as inputs or source nodes.
2. Review the included documents, assets, or source nodes and customise them to match your team, brand, or domain conventions where needed.
3. No specific AI provider or API key is required beyond your configured skrptiq LLM provider.

## Provider Notes

- Most stages work with any capable model; stronger models usually improve synthesis, judgement, and writing quality.
- Extraction, classification, and formatting steps generally run well on smaller or faster models.
- Because there are no vendor-specific integrations here, provider choice is mostly a trade-off between speed, quality, and cost.

## Example Input

To test this workflow immediately after import:

```
Complete Manuscript Draft: "Paste the relevant brief, notes, source material, or dataset here."
Target Journal Guidelines: "Paste the relevant brief, notes, source material, or dataset here."
Manuscript Abstract: "Paste the relevant brief, notes, source material, or dataset here."
Keywords: "growth, onboarding, retention"
```

