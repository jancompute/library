---
id: method:b-opsd
type: method
title: B-OPSD
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'privileged-teacher math OPSD with gold solutions (VISTA default)'
    reason: 'VISTA uses a gold solution; B-OPSD replaces the gold with a self-generated problem brief'
    use_instead: method:vista
  - when: 'unlabeled existing math problems with majority-vote pseudo-solutions'
    reason: 'u-OPSD is consensus pseudo-solutions; B-OPSD is a brief-conditioned privileged teacher without GT'
    use_instead: method:u-opsd
  - when: 'privileged retrospective distillation without GT or verifier rewards (RSD)'
    reason: 'RSD is retrospective self-distill; B-OPSD is live brief-conditioned OPSD'
    use_instead: method:rsd
assumptions:
  - 'No ground-truth solutions during training. Briefs are principles / applicability / pitfalls, not an answer. Qwen3 three sizes on AIME24 / AIME25 / HMMT25. Code ZevineXu/B-OPSD. Distinct from method:bopd (bootstrapped OPSD then OPD).'
last_reviewed: '2026-11-17'
papers:
- paper:b-opsd
recipes:
- recipe:b-opsd
claims:
- benchmark: 'AIME 2024 / AIME 2025 / HMMT 2025, Qwen3 three sizes'
  metric: 'average accuracy vs OPSD'
  value: 'both B-OPSD variants higher average accuracy than OPSD at each of three Qwen3 sizes; no GT during training'
  baseline: 'gold-conditioned OPSD'
  date: '2026-11-17'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.19273'
  notes: 'Does not retarget method:vista / method:u-opsd. Distinct slug from method:bopd.'
tags:
- opsd
- privileged-teacher
- label-free
- active
---

# B-OPSD

## Method Overview
B-OPSD (On-Policy Self-Distillation with Self-Generated Problem Briefs) drops the gold solution. A prompt template asks the initial model or a saved student checkpoint for principles, applicability conditions, and likely pitfalls — not a final answer. A frozen teacher uses that brief as privileged context and matches token distributions on the current student's on-policy rollouts.

## When to Use
- Privileged OPSD when you have questions but no gold solutions, and a short problem brief is a legal teacher context.

## When NOT to Use
Gold-solution OPSD remains `method:vista`. Unlabeled majority-vote remains `method:u-opsd`. Bootstrapped OPSD→OPD remains `method:bopd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:privileged-teacher-opsd`. Does **not** replace VISTA or u-OPSD.

## Gotchas & Failure Modes
- The brief must not leak a complete solution; the prompt forbids a final answer.
- Distinct slug from `method:bopd`.
