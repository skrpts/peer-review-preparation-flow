---
type: service
id: claude-service
title: Claude Service
description: "Anthropic Claude integration for manuscript review, journal analysis, and reviewer response drafting"
tags: [Production, Tested]
connections:
  - target: anthropic-claude
    type: runs_on
metadata:
  provider: anthropic
  model: claude-sonnet
---

## Service Description

This skrpt uses Anthropic Claude as the primary reasoning engine for manuscript preparation and peer review tasks. Claude handles self-critique, journal fit assessment, cover letter drafting, and response-to-reviewer composition.

## How This Skrpt Uses Claude

### Manuscript Self-Review
Claude performs a rigorous self-critique of the manuscript, evaluating it against common reviewer criteria: originality, methodology, clarity of writing, strength of evidence, and appropriateness of conclusions. It identifies weaknesses before peer reviewers do, giving the researcher an opportunity to address them proactively.

### Journal Fit Analysis
Claude assesses the alignment between a manuscript's topic, methodology, scope, and quality against the profiles of candidate journals. It considers impact factor, acceptance rates, typical article lengths, preferred methodologies, and recent publication patterns.

### Cover Letter Drafting
Claude drafts professional cover letters tailored to specific journals, highlighting the manuscript's contribution, novelty, and fit with the journal's scope and readership.

### Reviewer Response Crafting
Claude helps draft point-by-point responses to reviewer comments, ensuring each concern is addressed directly, respectfully, and with reference to specific changes made in the revised manuscript.

## Configuration

- **Model:** Claude Sonnet or higher for nuanced academic writing
- **Context window:** Extended context essential for processing full manuscripts and reviewer reports
- **Temperature:** 0.3 for self-critique, 0.4 for journal analysis, 0.5 for cover letters, 0.3 for reviewer responses
- **Output format:** Structured markdown with clear headings and point-by-point organisation
