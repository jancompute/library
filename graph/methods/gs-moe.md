---
id: method:gs-moe
type: method
title: 'GS-MoE'
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:pretrain-moe-frontier'
  reason: 'DeepSeek-V4 remains the MoE pretrain template; GS-MoE is post-hoc expert compression'
  use_instead: method:deepseek-v4
- when: 'training-free MoE expert prune by routing entropy (SPARE)'
  reason: 'SPARE allocates a prune budget from routing entropy; GS-MoE shares subspaces and prunes width'
  use_instead: method:spare-moe
assumptions:
- 'Calibrate then compress experts. Code cbacary/GS-MoE.'
last_reviewed: '2026-10-26'
papers:
- paper:gs-moe
recipes:
- recipe:gs-moe
claims:
- benchmark: 'Training-free MoE expert compression vs storing full experts'
  metric: 'memory of expert parameters vs quality after groupwise subspace share + width prune'
  value: 'groupwise shared subspace plus expert-width prune without retraining'
  baseline: 'uncompressed MoE; SPARE-style routing-entropy prune'
  date: '2026-10-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.32009'
  notes: 'Does not retarget method:deepseek-v4.'
tags:
- moe
- compression
- active
---

# GS-MoE

## Method Overview
GS-MoE compresses MoE experts without training by sharing groupwise low-rank subspaces and pruning expert width.

## When to Use
- A trained MoE whose expert storage is the bottleneck and retraining is off the table.

## When NOT to Use
Default on `task:pretrain-moe-frontier` remains `method:deepseek-v4`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:deepseek-v4`.

## Gotchas & Failure Modes
- Not a replacement for `method:deepseek-v4`.
- Paper claims are preprint-dated 2026-10-26; no locked-SOTA bake-off.
