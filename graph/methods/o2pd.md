---
id: method:o2pd
type: method
title: 'O2PD (Overlap-Gated Prefix Distillation)'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'choosing the single-teacher distillation algorithm'
  reason: 'OPD remains full-token reverse-KL matching; O2PD is a prefix + overlap-gated mix'
  use_instead: method:opd
- when: 'sparse OPD token selection by usefulness or IER'
  reason: 'O2PD uses a fixed prefix fraction, not a keep-mask'
  use_instead: method:sparse-opd-supervision
- when: 'verifiable labels exist and the goal is Pass@1 RLVR'
  reason: 'Labeled dense RLVR stays CISPO'
  use_instead: method:cispo
assumptions:
- 'VERL, k=16, DAPO-MATH-17K, prefix 20%. No public code as of 2026-11-06. arXiv 2611.07731 above watermark 2611.06911.'
last_reviewed: '2026-11-06'
papers:
- paper:o2pd
recipes:
- recipe:o2pd
claims:
- benchmark: 'Three student–teacher pairs, seven-suite Avg (Table 2)'
  metric: 'Avg vs OPD'
  value: 'Qwen3-1.7B←4B 26.80 (+1.89); DSR1-1.5B←JustRL-1.5B 39.48 (+4.81); 1.7B←4B-NTRL 50.58 (+5.29 vs OPD 45.29)'
  baseline: 'OPD / ESR / EOPD / TIP on the same pairs'
  date: '2026-11-06'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.07731'
  notes: 'Does not retarget method:opd. Prefix-20% plus overlap-gated alpha-divergence.'
tags:
- distillation
- opd
- active
---

# O2PD (Overlap-Gated Prefix Distillation)

## Method Overview
O²PD keeps reverse-KL OPD as the host and changes two things: only the first 20% of tokens in each trajectory receive the distill gradient, and the FKL/RKL mix is an overlap-gated $\alpha$-divergence with a reset atom and a support-convergence regularizer. Token count therefore scales with response length instead of a usefulness or entropy keep-mask.

## When to Use
- Same-tokenizer teacher OPD where full-token reverse-KL is noisy and a fixed prefix is acceptable.

## When NOT to Use
Default matching remains `method:opd`. Sparse keep-masks remain `method:sparse-opd-supervision` / `method:ier-opd`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:opd` or `method:open-mopd`.

## Gotchas & Failure Modes
- No public code; recipe is a sketch of the prefix + overlap gate.
- Paper Open-MOPD numbers are not the library 83.4% bake-off.
