---
id: method:uni-mopd
type: method
title: Uni-MOPD
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'multi-teacher on-policy distillation as the library bake-off'
    reason: 'Open-MOPD remains the 83.4% bake-off; Uni-MOPD is merge-then-short full-vocab reverse-KL on multimodal specialists'
    use_instead: method:open-mopd
  - when: 'same-tokenizer single-teacher matching distillation'
    reason: 'OPD remains the matching default; Uni-MOPD consolidates same-base specialists'
    use_instead: method:opd
  - when: 'branch-and-consolidate multi-teacher OPD of drifted specialists (BaC-MOPD; not Open-MOPD default)'
    reason: 'BaC-MOPD uses merge plus error-replay and balanced reverse-KL; Uni-MOPD uses uniform merge plus uniform sampling'
    use_instead: method:bac-mopd
  - when: 'training-free / forward-only fusion of same-base specialists'
    reason: 'Training-free OPD fuses without an update; Uni-MOPD still runs short MOPD after the merge'
    use_instead: method:training-free-opd
assumptions:
  - 'Same architecture and tokenizer as the specialists. Uniform DARE-style merge of same-base multimodal specialists, then short full-vocab reverse-KL with uniform domain sampling. Qwen3-VL-30B-A3B, five domains, 19 benches. Paper Open-MOPD is not the library 83.4% bake-off. Train framework announced; checkpoints AmberHeart/Uni-MOPD as of 2026-11-26.'
last_reviewed: '2026-11-26'
papers:
- paper:uni-mopd
recipes:
- recipe:uni-mopd
claims:
- benchmark: 'uniform merge vs base + 200 MOPD updates, before any Uni-MOPD training'
  metric: 'matched score'
  value: 'uniform merge matches 200 MOPD updates on the base before training'
  baseline: 'base + 200 MOPD updates'
  date: '2026-11-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.34397'
  notes: 'Start matters more than sampling/divergence. Paper Open-MOPD is not the library 83.4% bake-off.'
- benchmark: 'Uni-MOPD vs Open-MOPD at matched training budget, five multimodal domains / 19 benches'
  metric: 'wall-clock vs released Open-MOPD code; quality at matched budget'
  value: '3.3× faster; outperforms Open-MOPD at the same budget'
  baseline: 'Open-MOPD released code'
  date: '2026-11-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.34397'
  notes: 'Uniform sampling + full-vocab reverse KL. Distinct from BaC-MOPD. Does not retarget Open-MOPD.'
tags:
- distillation
- mopd
- merge
- active
---

# Uni-MOPD

## Method Overview
Uni-MOPD initializes the student with a training-free uniform merge of same-base specialists, then runs a short MOPD stage with uniform domain sampling and full-vocabulary reverse KL. No token-share schedules, per-token weights, or truncated vocab. The merge already matches hundreds of MOPD steps on a base init; short distillation closes remaining specialist gaps.

## When to Use
- Integrating same-base multimodal specialists where a uniform merge is a legal start and you can afford a short on-policy reverse-KL pass.

## When NOT to Use
Library multi-teacher bake-off remains `method:open-mopd`. Single-teacher matching remains `method:opd`. Drifted-specialist consolidation with error-replay remains `method:bac-mopd`. Merge-only fusion remains `method:training-free-opd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:student-distillation`. Paper Open-MOPD numbers are not the library 83.4% bake-off. Distinct from BaC-MOPD / training-free OPD / C-MOPD / RDS-MOPD. Does **not** replace Open-MOPD or OPD.

## Gotchas & Failure Modes
- Train framework announced, not released (`code_status: announced`). Checkpoints on Hugging Face.
- Merge-only is not the final model; short MOPD still recovers unintegrated domains.
- Requires specialists from the same base; not a cross-tokenizer recipe.
