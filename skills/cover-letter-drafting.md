---
type: skill
id: cover-letter-drafting
title: Cover Letter Drafting
description: "Drafting a professional, journal-specific submission cover letter tailored to the target journal and manuscript"
tags: [Production, Academic, Communication]
connections:
  - target: llm-service
    type: runs_on
metadata:
  estimated_duration: "5 minutes"
  avg_tokens: 2000
  trigger: manual
---

## Cover Letter Drafting

This skill produces the submission cover letter — the editor's first impression of the work — tailored to the selected journal and grounded in the preparation completed upstream.

### Core Capability

Given the journal recommendations and the self-critique as context, plus the manuscript metadata as inputs, this skill drafts a concise, persuasive cover letter that states the contribution, justifies the fit with the target journal, and includes the required compliance statements.

### Method

1. **Framing:** Open with the editor, manuscript title and type, and the specific target journal drawn from the journal recommendations.
2. **Significance:** State the research problem, headline findings, and what is genuinely novel — informed by the self-critique so claims are neither overstated nor undersold.
3. **Fit and compliance:** Justify the fit with the journal's scope and add the applicable compliance statements (exclusivity, author approval, conflicts, ethics, AI disclosure).

### Output Structure

A complete, one-page cover letter in professional letter format. This is the primary submission deliverable and the final content artefact before language polishing.
