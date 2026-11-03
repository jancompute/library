---
id: method:sonar-moe
type: method
title: 'Sonar-MoE'
category: optimizer
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:full-param-memory-efficient-pretrain'
  reason: 'SCALE remains mem-efficient dense pretrain; Sonar-MoE is MoE in-backward experts'
  use_instead: method:scale
assumptions:
- 'OLMoE-1B-7B and Granite-3.1-3B-A800M bf16, two expert-kernel backends. No public code as of 2026-11-03.'
last_reviewed: '2026-11-03'
papers:
- paper:sonar-moe
recipes:
- recipe:sonar-moe
claims:
- benchmark: 'OLMoE-1B-7B and Granite-3.1-3B-A800M bf16 fine-tune'
  metric: 'peak memory / step time / loss vs standard MoE'
  value: '19-22% peak mem; 17-23% faster than global-norm clip; loss within 0.003; bitwise-identical without expert clip'
  baseline: 'standard MoE training with expert gradients held to the optimizer step'
  date: '2026-11-03'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.03577'
  notes: 'Does not retarget method:scale. Distinct from method:duplextune.'
tags:
- moe
- memory
- active
---

# Sonar-MoE

## Method Overview
Sonar-MoE applies optimizer-in-backward to batched MoE expert tensors so expert gradients never accumulate across the model.

## When to Use
- MoE fine-tune or pretrain where expert gradients dominate peak memory.

## When NOT to Use
SCALE remains mem-efficient dense pretrain. DuplexTune is coupled-state replay, not in-backward experts.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:scale`.

## Gotchas & Failure Modes
- Bitwise identity drops if you clip expert gradients.
- No public code as of 2026-11-03.
- Paper claims are dated 2026-11-03; no locked-SOTA bake-off.
