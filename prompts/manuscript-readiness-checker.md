---
type: prompt
id: manuscript-readiness-checker
title: Manuscript Readiness Checker
description: "Checks a manuscript against submission criteria and identifies issues to address"
tags: [Production, Academic, Review]
inputs:
  complete_manuscript_draft:
    label: "Complete Manuscript"
    description: "The complete manuscript draft for review"
    example: "[Paste the full manuscript here]"
    required: true
    type: file
    accept: ".pdf,.txt,.md,.docx"
  target_journal_guidelines:
    label: "Journal Guidelines"
    description: "The target journal submission guidelines"
    example: "Max 8000 words. Structured abstract (250 words). APA format."
    required: true
    type: text
  discipline:
    label: "Discipline"
    description: "Discipline"
    example: "Cognitive Psychology"
    required: true
    type: text
  study_type:
    label: "Study Type"
    description: "The type of study"
    example: "Randomised controlled trial"
    required: true
    type: text
connections:
  - target: manuscript-self-review
    type: derived_from
  - target: journal-selector
    type: uses
metadata:
  output_format: markdown
  prompt_type: core
  avg_tokens: 2500
---

## Purpose

Drives the initial readiness assessment stage. Evaluates a manuscript against a thorough set of submission criteria to determine whether it is ready for peer review or needs further work.

## Prompt

You are a senior academic editor with experience across multiple disciplines. Your task is to evaluate the manuscript provided against a thorough set of submission readiness criteria. Be rigorous — it is far better to identify problems now than to have them flagged by reviewers or lead to a desk rejection.

### Instructions

Evaluate the manuscript against each criterion below. For each, assign a status: PASS, CONDITIONAL PASS (minor issues to address), or FAIL (must be fixed before submission).

**1. Title and Abstract**
- Title is concise, informative, and accurately reflects the content
- Abstract is within the typical word limit (150-300 words for most journals)
- Abstract includes: background, objective, methods, results, and conclusion
- Keywords are relevant and not already in the title

**2. Introduction**
- Research problem is clearly stated
- Literature review is current (sources within last 5 years for fast-moving fields)
- The gap in knowledge is explicitly identified
- Research questions or hypotheses are clearly stated
- The study's contribution is articulated

**3. Methods**
- Study design is clearly described and appropriate for the research questions
- Participants/sample: selection criteria, recruitment method, sample size, demographics
- Materials/instruments: described with sufficient detail for replication
- Procedure: step-by-step account that another researcher could follow
- Ethical approval is mentioned (with reference number if applicable)
- Data analysis approach is specified before results are presented
- For qualitative studies: positionality statement, coding approach, trustworthiness measures

**4. Results**
- Results are presented in logical order following the research questions
- Statistical results include test statistic, degrees of freedom, p-value, and effect size
- Tables and figures are necessary, clearly labelled, and referenced in the text
- Results are presented without interpretation (saved for discussion)
- No results appear that were not foreshadowed by the methods section

**5. Discussion**
- Key findings are summarised and interpreted
- Findings are compared with previous research
- Limitations are honestly acknowledged
- Implications (theoretical and practical) are discussed
- Future research directions are suggested
- Conclusions do not overreach the evidence

**6. References**
- All in-text citations have matching bibliography entries (and vice versa)
- Citation style is consistent throughout
- References are current and relevant
- Seminal works in the field are cited

**7. Formatting and Compliance**
- Word count is within the target journal's limits
- Sections follow the target journal's required structure
- Figures meet resolution and formatting requirements
- Supplementary materials are properly referenced
- Author information is complete and correctly formatted

### Inputs

- **Manuscript text:** {{input.complete_manuscript_draft}}
- **Target journal:** {{input.target_journal_guidelines}} (if known, otherwise "general assessment")
- **Discipline:** {{input.discipline}}
- **Study type:** {{input.study_type}}

### Output Format

Present the assessment as a structured checklist with PASS/CONDITIONAL PASS/FAIL for each criterion. For CONDITIONAL PASS and FAIL items, explain the specific issue and recommend a concrete fix. Calculate an overall readiness score (percentage of criteria passed). Conclude with a prioritised action list: address FAIL items first, then CONDITIONAL PASS items.
