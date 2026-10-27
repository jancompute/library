---
id: method:skill-adaptation
type: method
title: 'Skill Adaptation'
category: agent-harness
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:agent-harness-runtime'
  reason: 'omp2 remains the production kernel; skill adaptation rewrites harness skills to the executor'
  use_instead: method:omp2-harness
assumptions:
- 'Harness self-evolution via skill rewrite. Project page announced. HF Daily 2026-10-27.'
last_reviewed: '2026-10-27'
papers:
- paper:skill-adaptation
recipes:
- recipe:skill-adaptation
claims:
- benchmark: 'Seven models / three benches skill transfer vs unadapted skills'
  metric: 'task points; failure when the skill already states the requirement'
  value: '103 pairs: GPT-5.6-luna +31.1 vs Gemma-4-E4B -8.8; 86% of weak failures already named in the skill'
  baseline: 'unadapted transferred harness skills'
  date: '2026-10-27'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.33024'
  notes: 'Does not retarget method:omp2-harness.'
tags:
- agent-harness
- active
---

# Skill Adaptation

## Method Overview
Skill adaptation rewrites existing harness skills so a weaker executor can actually follow them, instead of copying skills that only a stronger model can execute.

## When to Use
- Frozen-weight harness RSI where skills written for a stronger model degrade a weaker one.

## When NOT to Use
Default on `task:agent-harness-runtime` remains `method:omp2-harness`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:omp2-harness`.

## Gotchas & Failure Modes
- Not a replacement for `method:omp2-harness`.
- Paper claims are preprint-dated 2026-10-27; no locked-SOTA bake-off.
