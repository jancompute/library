---
id: method:p2-mopd
type: method
title: 'P2-MOPD (Parameter-Prior Multi-Teacher OPD)'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'choosing the multi-teacher distillation algorithm'
  reason: 'Open-MOPD remains token-share / gap-aware budget; P2-MOPD treats experts as trainable mixing coefficients'
  use_instead: method:open-mopd
- when: 'choosing the single-teacher distillation algorithm'
  reason: 'OPD remains matching; P2-MOPD is multi-teacher parameter priors'
  use_instead: method:opd
- when: 'token-level ExpertAlign routing over unlabeled multi-teacher pools'
  reason: 'MOPD-Router routes the pool per token; P2-MOPD mixes expert parameters'
  use_instead: method:mopd-router
- when: 'DRO domain-mixture scheduling for multi-teacher OPD (RDS-MOPD)'
  reason: 'P2-MOPD mixes expert parameters; RDS-MOPD reallocates prompt shares under DRO'
  use_instead: method:rds-mopd
assumptions:
- 'Labeled domain experts plus a student under live OPD. Paper: 1.7B / 4B, four domains. GitHub SinuoWang/P2-MOPD is README-only as of 2026-11-09 (code_status: announced). Paper Open-MOPD is not the library 83.4% bake-off. arXiv 2611.03953 is an HF Daily leftover below listing watermark 2611.08453.'
last_reviewed: '2026-11-09'
papers:
- paper:p2-mopd
recipes:
- recipe:p2-mopd
claims:
- benchmark: 'Four-domain average recovery at 1.7B / 4B (Table 1)'
  metric: 'avg recovery vs MOPD'
  value: '1.7B 94.7% vs MOPD 80.9%; 4B 94.9% (+8.9 vs MOPD); surpasses MOPD final recovery in half the steps'
  baseline: 'MOPD / MOPD (SFT warm-up) / IM-MOPD / task arithmetic'
  date: '2026-11-09'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.03953'
  notes: 'Does not retarget method:open-mopd. Worst-domain recovery from below 50% to about 90%. Paper Open-MOPD numbers are not the library 83.4% bake-off.'
tags:
- distillation
- mopd
- active
---

# P2-MOPD (Parameter-Prior Multi-Teacher OPD)

## Method Overview
P²-MOPD jointly optimizes mixing coefficients over expert task vectors and the student weights under the same on-policy distillation objective. Experts are parameter priors; the student is not confined to the frozen linear span used by task arithmetic.

## When to Use
- Multi-teacher OPD from domain specialists when token-share MOPD recovers slowly on the lagging domain.

## When NOT to Use
Multi-teacher default remains `method:open-mopd`. Single-teacher matching remains `method:opd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation`. Does **not** replace Open-MOPD.

## Gotchas & Failure Modes
- Announced GitHub is README-only; do not assume a trainer is runnable.
- Extra actor-update cost streams the task vectors; rollout generation is unchanged.
