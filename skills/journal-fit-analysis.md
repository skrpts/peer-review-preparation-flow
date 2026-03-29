---
type: skill
id: journal-fit-analysis
title: Journal Fit Analysis
description: "Analyses the fit between a manuscript and potential target journals for submission"
tags: [Production, Tested, Academic, Review]
connections:
  - target: llm-service
    type: runs_on
  - target: journal-submission-standards
    type: references
metadata:
  estimated_duration: "15-25 minutes"
  avg_tokens: 2500
---

## Capability

Assesses how well a manuscript aligns with the scope, standards, and preferences of potential target journals. This skill evaluates multiple dimensions of fit — topical relevance, methodological alignment, quality expectations, and practical considerations — to produce a ranked list of recommended journals with detailed justifications.

## When to Use

- Choosing where to submit a new manuscript
- Deciding where to resubmit after a rejection
- Evaluating whether a manuscript needs repositioning for a different journal tier
- Comparing open access and subscription journal options
- Assessing whether a manuscript's scope matches a journal's recent publication trends

## Inputs

- Manuscript abstract and keywords
- Research methodology and study type
- Field and sub-discipline
- Author preferences: impact factor range, open access requirements, geographic preferences, turnaround time expectations, page charges budget
- List of journals to evaluate (or request for the skill to suggest journals based on the manuscript's profile)
- Any journals to exclude (e.g., previously rejected from)

## Process

1. **Scope alignment** — assess whether the manuscript's topic falls within each journal's stated aims and scope. Check recent issues (last 2-3 years) for similar topics
2. **Methodological fit** — evaluate whether the journal publishes the type of research presented (qualitative, quantitative, mixed methods, theoretical, review). Some journals favour specific methodological approaches
3. **Quality calibration** — assess whether the manuscript's rigour, sample size, novelty, and contribution match the journal's typical publication standards. Consider rejection rates as a proxy for selectivity
4. **Audience alignment** — consider whether the journal's readership matches the intended audience for the manuscript. A highly specialised finding may be better suited to a niche journal than a generalist one, or vice versa
5. **Practical factors** — evaluate turnaround time, publication fees (APCs for open access), word count limits, formatting requirements, and the journal's backlog
6. **Rejection risk assessment** — identify specific factors that could lead to a desk rejection at each journal (outside scope, wrong methodology type, insufficient novelty for the tier)
7. **Strategic considerations** — factor in career stage considerations, funder requirements for open access, and the strategic value of publishing in specific venues

## Outputs

- Ranked list of 5-8 recommended journals with fit scores (0-100)
- For each journal: scope alignment, methodological fit, quality calibration, practical considerations, and key risks
- Recommended submission order (where to try first, and fallback options)
- Specific formatting or content adjustments needed for each target journal

## Constraints

- Base journal recommendations on the manuscript's actual quality, not aspirational targets — submitting to an unrealistically prestigious journal wastes time
- Always include at least one "stretch" journal and one "safety" journal alongside the recommended targets
- Acknowledge uncertainty: journal acceptance is inherently unpredictable, and fit analysis is a probability assessment, not a guarantee
- Consider open access mandates from funders and institutions
- Never recommend predatory journals — flag any journals on known predatory journal lists
