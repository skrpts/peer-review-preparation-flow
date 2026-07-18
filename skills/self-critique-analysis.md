---
type: skill
id: self-critique-analysis
title: Self-Critique Analysis
description: "Producing a rigorous, reviewer-style self-critique that anticipates likely objections before submission"
tags: [Production, Academic, Review]
connections:
  - target: llm-service
    type: runs_on
metadata:
  estimated_duration: "6 minutes"
  avg_tokens: 3000
  trigger: manual
---

## Self-Critique Analysis

This skill simulates the peer review process before external reviewers see the manuscript, surfacing genuine weaknesses while they can still be addressed.

### Core Capability

Given the manuscript readiness assessment and the shortlisted journal recommendations as context, this skill adopts multiple reviewer personas — methodologist, domain expert, and writing critic — and produces honest, prioritised feedback grounded in the manuscript itself.

### Method

1. **Multi-persona review:** Assess research design, theoretical contribution, and presentation from three distinct reviewer perspectives.
2. **Severity grading:** Label every comment MAJOR or MINOR, with a recommended action and the likely consequence if left unaddressed.
3. **Synthesis:** Distil the most critical cross-reviewer issues into a priority-ordered action list and an overall submit / revise / rework recommendation.

### Output Structure

A structured critique with a section per reviewer persona followed by a synthesis. The critique feeds the cover-letter stage downstream, ensuring the submission reflects a manuscript that has already survived internal scrutiny.
