---
type: skill
id: manuscript-self-review
title: Manuscript Self-Review
description: "Performs rigorous self-review of academic manuscripts against peer review criteria"
tags: [Production, Tested]
connections:
  - target: llm-service
    type: runs_on
  - target: journal-submission-standards
    type: references
metadata:
  estimated_duration: "20-30 minutes"
  avg_tokens: 3000
---

## Capability

Performs a thorough self-review of an academic manuscript, evaluating it against the criteria that peer reviewers and editors typically use when assessing submissions. This skill identifies weaknesses, gaps, and potential objections before the manuscript reaches external reviewers, giving the researcher an opportunity to strengthen their work proactively. The review covers structural completeness, methodological rigour, writing quality, argument strength, and journal-specific requirements.

## When to Use

- Before submitting a manuscript to a journal for peer review
- After completing a major revision and before resubmission
- When seeking an objective assessment of a manuscript draft's strengths and weaknesses
- When preparing a manuscript for co-author review
- When checking whether a manuscript meets a specific journal's submission guidelines

## Inputs

- Complete manuscript text (all sections including abstract, introduction, methods, results, discussion, references)
- Target journal name and guidelines (if known)
- Field of study and sub-discipline
- Study type (experimental, observational, qualitative, mixed methods, theoretical, review)
- Any specific concerns the researcher wants addressed

## Process

1. **Structural completeness** — verify all required sections are present and appropriately developed. Check that the abstract accurately summarises the full paper. Confirm that the introduction establishes the gap, the methods are reproducible, the results answer the research questions, and the discussion interprets the findings
2. **Methodological assessment** — evaluate the rigour of the research design, sampling strategy, data collection, and analysis. Identify potential threats to internal and external validity. Check whether limitations are adequately acknowledged
3. **Argument coherence** — trace the logical thread from research questions through findings to conclusions. Identify any logical leaps, unsupported claims, or conclusions that overreach the evidence
4. **Writing quality** — assess clarity, conciseness, and academic tone. Flag jargon that is not defined, sentences that are unnecessarily complex, and paragraphs that lack clear topic sentences
5. **Citation adequacy** — check that key claims are supported by citations, that the literature review is current and balanced, and that seminal works in the field are referenced
6. **Figure and table quality** — evaluate whether figures and tables are necessary, clear, correctly labelled, and referenced in the text
7. **Journal fit** — if a target journal is specified, assess the manuscript against journal-specific requirements (word count, structure, reference format, reporting guidelines)

## Outputs

- Section-by-section assessment with specific strengths and weaknesses
- Prioritised list of recommended revisions (critical, major, minor)
- Readiness score (0-100) indicating overall submission readiness
- Anticipated reviewer objections with suggested pre-emptive responses
- Journal-specific compliance checklist (if target journal is specified)

## Constraints

- Be genuinely critical — the purpose is to identify real weaknesses, not to reassure the researcher
- Distinguish between issues that would likely lead to rejection (critical) and those that would prompt revision requests (major/minor)
- Do not suggest changes that would misrepresent the research or inflate the findings
- Acknowledge the difference between what can be fixed in writing (clarity, structure) and what reflects genuine study limitations (sample size, design choices)
- Frame all feedback constructively — explain why something is a problem and how to fix it
