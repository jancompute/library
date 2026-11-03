---
id: method:paretosaddler
type: method
title: 'ParetoSaddler'
category: agent-harness
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:agent-harness-runtime'
  reason: 'omp2 remains the production kernel; ParetoSaddler is quality+cost harness search'
  use_instead: method:omp2-harness
assumptions:
- 'Domain-disjoint ClawMark / GAIA2 splits. Sibling of ActiveSaddler. Code announced.'
last_reviewed: '2026-11-03'
papers:
- paper:paretosaddler
recipes:
- recipe:paretosaddler
claims:
- benchmark: 'ClawMark / GAIA2, domain-disjoint splits'
  metric: 'quality and cost per task'
  value: 'ClawMark 70.86 to 81.35% and $1.17 to $1.01; GAIA2 56.22 to 62.89% and $0.78 to $0.45'
  baseline: 'quality-only harness optimization'
  date: '2026-11-03'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.02079'
  notes: 'Does not retarget method:omp2-harness. Sibling of method:activesaddler.'
tags:
- harness
- pareto
- active
---

# ParetoSaddler

## Method Overview
ParetoSaddler promotes harness rewrites that credibly improve quality or cost, keeping those parents around, and only applies the deployment preference at the end.

## When to Use
- Harness RSI where cost and quality both matter and early cost filters would kill useful parents.

## When NOT to Use
omp2 remains the production kernel. ActiveSaddler remains failure-pattern curriculum.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:omp2-harness` or `method:activesaddler`.

## Gotchas & Failure Modes
- Code announced at aka.ms/ParetoSaddler-website, not a released GitHub as of 2026-11-03.
- Paper claims are dated 2026-11-03; no locked-SOTA bake-off.
