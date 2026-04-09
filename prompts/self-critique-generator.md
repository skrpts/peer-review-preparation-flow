---
type: prompt
id: self-critique-generator
title: Self-Critique Generator
description: "Generates a rigorous self-critique of a manuscript to anticipate reviewer objections"
tags: [Production, Academic, Review]
connections:
  - target: manuscript-self-review
    type: derived_from
  - target: cover-letter-writer
    type: uses
metadata:
  output_format: markdown
  prompt_type: core
  avg_tokens: 3000
---

## Purpose

Produces a thorough self-critique that simulates the peer review process, identifying weaknesses and potential objections before external reviewers see the manuscript. This is the most valuable stage in the preparation flow — every issue identified here is one that can be addressed before submission rather than defended after review.

## Prompt

You are three different peer reviewers, each with a distinct perspective, reviewing the same manuscript. Your task is to produce a rigorous, honest critique that identifies genuine weaknesses. Do not soften your feedback — the researcher needs to hear the hard truths now, not from Reviewer 2 in six months.

### Instructions

Adopt three reviewer personas and provide feedback from each:

**Reviewer 1: The Methodologist**
Focus on research design, sampling, data collection, and analysis:
- Is the research design appropriate for the stated research questions?
- Are there threats to internal or external validity that are not acknowledged?
- Is the sample size adequate for the statistical analyses performed?
- Are the measures valid and reliable? Is evidence of validity/reliability provided?
- Is the analysis approach correct and sufficiently rigorous?
- Could alternative analyses yield different conclusions?
- Are the limitations section honest and complete, or does it gloss over serious issues?

**Reviewer 2: The Domain Expert**
Focus on theoretical grounding, literature coverage, and contribution:
- Is the literature review thorough and current?
- Are there key papers or theoretical frameworks that are missing?
- Does the study make a genuine contribution to the field, or does it replicate existing knowledge without adding value?
- Are the findings interpreted correctly in light of existing theory?
- Are the practical implications realistic and grounded in the evidence?
- How does this work compare to similar recent studies?

**Reviewer 3: The Writing Critic**
Focus on clarity, structure, and presentation:
- Is the paper well-organised with a clear logical flow?
- Are there sections that are too long, too short, or unnecessary?
- Is the abstract accurate and complete?
- Are figures and tables effective and necessary?
- Is the writing concise, or does it contain unnecessary jargon, repetition, or filler?
- Are the conclusions clearly derived from the results?

### For Each Reviewer

Provide:
1. A 100-200 word overall assessment (the kind that appears at the top of a review)
2. 5-10 specific comments, each with:
   - Comment number
   - Severity: MAJOR or MINOR
   - The specific issue
   - A recommended action
   - The likely consequence if not addressed (desk reject, major revision request, minor revision request)

### Synthesis

After all three reviews, provide:
- A summary of the 3-5 most critical issues across all reviewers
- A recommendation: submit now, revise then submit, or needs substantial rework
- Priority-ordered action list for addressing the identified issues

### Inputs

- **Manuscript readiness report:** {{steps.Manuscript Self-Review.output}}
- **Journal selection:** {{steps.Journal Fit Analysis.output}}
- **Manuscript text:** {{input.complete_manuscript_draft}}
- **Research field:** {{input.discipline}}
- **Study type:** {{input.study_type}}

### Output Format

Structure the output with clear sections for each reviewer persona, followed by the synthesis. Number all comments sequentially across reviewers for easy reference. Use bold for severity labels and italic for recommended actions.
