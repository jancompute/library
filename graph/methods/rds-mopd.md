---
id: method:rds-mopd
type: method
title: 'RDS-MOPD (Robust Domain-Mixture Scheduling)'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'choosing the multi-teacher distillation algorithm'
  reason: 'Open-MOPD remains token-share / gap-aware budget; RDS-MOPD is DRO mixture under noisy KL'
  use_instead: method:open-mopd
- when: 'choosing the single-teacher distillation algorithm'
  reason: 'OPD remains matching; RDS-MOPD schedules domain shares across teachers'
  use_instead: method:opd
- when: 'parameter-prior MOPD (experts as trainable mixing coefficients; P2-MOPD)'
  reason: 'P2-MOPD mixes expert parameters; RDS-MOPD reallocates prompt shares'
  use_instead: method:p2-mopd
assumptions:
- 'Labeled domain teachers plus live reverse-KL OPD. Paper: SmolLM3-3B MixSFT student, Open-MOPD RL-Math/Code/IF teachers, 150 steps, 1024 prompts/step, schedule every 10 steps. Paper Open-MOPD is not the library 83.4% bake-off. No public code as of 2026-11-10. arXiv 2611.12012 above watermark 2611.09634.'
last_reviewed: '2026-11-10'
papers:
- paper:rds-mopd
recipes:
- recipe:rds-mopd
claims:
- benchmark: 'SmolLM3-3B six-bench MOPD (AIME24/25, LCB v5/v6, IFEval/IFBench)'
  metric: 'BO Avg. Rank / recovery vs Open-MOPD / D3-MOPD'
  value: 'rank 1.50 / recovery 118.1% vs Open-MOPD 2.67 / 105.6 and D3-MOPD 2.58 / 106.5; AIME24 26.72 vs 24.77'
  baseline: 'Open-MOPD / D3-MOPD / Vanilla DRO-MOPD / Vanilla MOPD'
  date: '2026-11-10'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.12012'
  notes: 'Does not retarget method:open-mopd. Paper Open-MOPD is not the library 83.4% bake-off.'
tags:
- distillation
- mopd
- dro
- active
---

# RDS-MOPD (Robust Domain-Mixture Scheduling)

## Method Overview
RDS-MOPD allocates the shared MOPD prompt budget with DRO, but only moves share when the per-domain KL gap exceeds an online noise floor, clips KL spikes in log-Huber, and defines the worst case as regression from each domain's own best level.

## When to Use
- Multi-teacher OPD where progress-driven mixers starve a lagging domain or lock onto a noisy KL spike.

## When NOT to Use
Multi-teacher default remains `method:open-mopd`. Single-teacher matching remains `method:opd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation`. Does **not** replace Open-MOPD.

## Gotchas & Failure Modes
- No public trainer; reimplement on the Open-MOPD host (top-16 reverse KL, mixture `q` over prompt sampling).
- Vanilla DRO without NRC/SAE/WDR is worse than Open-MOPD on four of six benches.
- Paper Open-MOPD numbers are not the library 83.4% bake-off.
