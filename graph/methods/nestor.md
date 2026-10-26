---
id: method:nestor
type: method
title: 'NESTOR'
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:pretrain-dense-7b'
  reason: 'Muon2 remains the ~7B optimizer; NESTOR is nested conditional-computation sparsity, not an optimizer'
  use_instead: method:muon2
- when: 'the locked first hop on task:pretrain-moe-frontier'
  reason: 'NESTOR is nested sparsity; DeepSeek-V4 / Kimi-K3 remain the MoE template'
  use_instead: method:deepseek-v4
- when: 'multi-stage agent capability stacking / ACLArena'
  reason: 'ACLArena remains agent continual-learning; NESTOR is nested-sparsity architecture'
  use_instead: method:aclarena
assumptions:
- 'MoE-style nested sparsity. Code Ma-Lab-Berkeley/Nestor.'
last_reviewed: '2026-10-26'
papers:
- paper:nestor
recipes:
- recipe:nestor
claims:
- benchmark: 'Nested-sparsity pretrain and continual learning vs standard MoE conditional compute'
  metric: 'scalable pretrain / continual-learning compute vs dense or flat MoE'
  value: 'nested sparsity as an alternative conditional-compute axis to MoE FFNs'
  baseline: 'dense Transformer; standard MoE FFN routing'
  date: '2026-10-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.31818'
  notes: 'Does not retarget method:muon2.'
tags:
- architecture
- sparsity
- active
---

# NESTOR

## Method Overview
NESTOR explores nested sparsity as conditional computation outside the MoE FFN, for pretraining and continual learning.

## When to Use
- Pretrain or continual-learning runs that want nested conditional compute rather than a flat MoE FFN.

## When NOT to Use
Default on `task:pretrain-dense-7b` remains `method:muon2`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:muon2`.

## Gotchas & Failure Modes
- Not a replacement for `method:muon2`.
- Paper claims are preprint-dated 2026-10-26; no locked-SOTA bake-off.
