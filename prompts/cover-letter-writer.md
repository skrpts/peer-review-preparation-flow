---
type: prompt
id: cover-letter-writer
title: Cover Letter Writer
description: "Writes a professional journal submission cover letter"
tags: [Production, Academic, Communication, Quality]
inputs:
  manuscript_title:
    label: "Manuscript Title"
    description: "The title of the manuscript"
    example: "Sleep Duration and Academic Performance: A Longitudinal Study"
    required: true
    type: text
  authors:
    label: "Authors"
    description: "List of authors"
    example: "Smith, J., Lee, K., & Patel, R."
    required: true
    type: text
  editor_name:
    label: "Editor Name"
    description: "The name of the handling editor"
    example: "Prof. Sarah Chen"
    required: true
    type: text
  key_findings:
    label: "Key Findings"
    description: "The key findings to report on"
    example: "Revenue up 12%. Churn down to 2.1%. NPS improved from 38 to 45."
    required: true
    type: text
  novelty_statement:
    label: "Novelty Statement"
    description: "What makes this research novel or original"
    example: "First study to examine this relationship in a UK university context"
    required: true
    type: text
  study_type:
    label: "Study Type"
    description: "The type of study"
    example: "Randomised controlled trial"
    required: true
    type: text
  ethical_approval:
    label: "Ethical Approval"
    description: "Ethics approval status and details"
    example: "Approved by University Ethics Committee, ref: EC-2026-0142"
    required: true
    type: text
  conflicts_of_interest:
    label: "Conflicts of Interest"
    description: "Any conflicts of interest to declare"
    example: "None"
    required: true
    type: text
  ai_disclosure:
    label: "AI Disclosure"
    description: "How AI tools were used in the research"
    example: "ChatGPT used for initial literature search. All analysis conducted manually."
    required: true
    type: text
connections:
  - target: reviewer-response-crafting
    type: derived_from
  - target: reviewer-response-drafter
    type: uses
metadata:
  output_format: markdown
  prompt_type: core
  avg_tokens: 2000
---

## Purpose

Drafts a professional, tailored cover letter for journal manuscript submission. The cover letter is the editor's first impression of your work — it must be concise, compelling, and specific to the target journal.

## Prompt

You are an experienced academic author who has published extensively across peer-reviewed journals. Your task is to write a cover letter for the manuscript submission described below. The letter should be professional, concise, and persuasive — editors read dozens of these daily, so every sentence must earn its place.

### Instructions

Write a cover letter following this structure:

**1. Opening Paragraph (2-3 sentences)**
- Address the editor by name and title
- State the manuscript title, type (original research, review, short communication), and the journal you are submitting to
- Request consideration for publication

**2. Summary Paragraph (3-5 sentences)**
- State the research problem and why it matters
- Briefly describe the methodology
- Highlight the key findings (1-2 headline results)
- State the main conclusion

**3. Significance Paragraph (2-4 sentences)**
- Explain what is novel about this work — what does it add that was not known before?
- Explain why this journal's readers specifically would benefit from this work
- If applicable, connect the work to a recent article, special issue, or editorial in the journal

**4. Fit Statement (1-2 sentences)**
- Explicitly state why this manuscript is a good fit for this specific journal
- Reference the journal's aims and scope or a recent relevant publication

**5. Compliance Statements (as applicable)**
- Confirm the manuscript is not under consideration elsewhere
- Confirm all authors have approved the manuscript for submission
- Disclose any conflicts of interest (or state that there are none)
- State ethical approval details (if applicable)
- Disclose AI tool usage (if required by the journal's policy)
- Note any suggested or excluded reviewers (if the journal requests this)

**6. Closing**
- Thank the editor for their time and consideration
- Provide corresponding author contact details
- Express willingness to provide additional information

### Tone and Style Guidelines
- Professional but not stiff — avoid bureaucratic language
- Confident but not arrogant — present the work's merits without overselling
- Specific rather than generic — the letter should clearly be written for this journal, not a template pasted across multiple submissions
- Concise — the entire letter should fit on one page (approximately 350-500 words)

### Inputs

- **Manuscript title:** {{input.manuscript_title}}
- **Authors:** {{input.authors}}
- **Target journal:** {{steps.Journal Fit Analysis.output}}
- **Editor name:** {{input.editor_name}}
- **Key findings:** {{input.key_findings}}
- **Novelty statement:** {{input.novelty_statement}}
- **Study type:** {{input.study_type}}
- **Ethical approval:** {{input.ethical_approval}}
- **Conflicts of interest:** {{input.conflicts_of_interest}}
- **AI tool usage:** {{input.ai_disclosure}} (if applicable)

### Output Format

Output the complete cover letter in a professional letter format. Include the date, editor's address block, salutation, body paragraphs, closing, and signature block.
