---
id: method:topsd
type: method
title: 'TOPSD (Teachable On-Policy Self-Distillation)'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'gold-solution privileged OPSD as the trainer'
  reason: 'VISTA remains privileged-teacher first hop; TOPSD gates prefixes against Teacher Drift'
  use_instead: method:vista
- when: 'in-language (L2) reasoning SFT rather than privileged OPSD'
  reason: 'Tiny Aya L2-Thinker remains the L2 SFT first hop; TOPSD is multilingual math OPSD'
  use_instead: method:tiny-aya-l2-thinker
- when: 'choosing the single-teacher distillation algorithm'
  reason: 'OPD remains matching; TOPSD is privileged OPSD with recoverability checks'
  use_instead: method:opd
assumptions:
- 'Fixed privileged teacher, full-vocabulary logit distill. Paper: Qwen3-1.7B/4B/8B, PolyMath High ten languages, Avg@3 / Pass@3, K=4 persistence. No public code as of 2026-11-09. arXiv 2611.08179 is an HF Daily leftover after watermark 2611.06911, not in Friday SKIP.'
last_reviewed: '2026-11-09'
papers:
- paper:topsd
recipes:
- recipe:topsd
claims:
- benchmark: 'PolyMath High Avg@3, Qwen3-1.7B / 4B / 8B, ten languages (Table 1)'
  metric: 'Avg@3 vs strongest baseline'
  value: '11.60 / 17.79 / 25.12 (+1.65 / +1.07 / +2.64); Pass@3 18.72 / 26.00 / 35.28'
  baseline: 'OPSD / COPSD'
  date: '2026-11-09'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.08179'
  notes: 'Does not retarget method:vista. Supervising failed-recovery prefixes is worse than supervising all selected prefixes.'
tags:
- distillation
- opsd
- multilingual
- active
---

# TOPSD (Teachable On-Policy Self-Distillation)

## Method Overview
A privileged teacher that conditions on a student prefix can follow the student's accumulating errors (Teacher Drift). TOPSD keeps only teachable prefixes and verifies that the teacher can recover from those prefixes before applying the OPSD update.

## When to Use
- Privileged OPSD on multilingual math traces where the teacher starts copying student mistakes.

## When NOT to Use
Privileged-teacher first hop remains `method:vista`. L2 reasoning SFT remains `method:tiny-aya-l2-thinker`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:privileged-teacher-opsd` with a mention on `task:multilingual-l2-reasoning-sft`. Does **not** replace VISTA.

## Gotchas & Failure Modes
- No public code.
- Prefix selection without recoverability verification is weaker; failed-recovery prefixes hurt.
