---
id: method:ciga
type: method
title: 'CIGA'
category: data-attribution
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:training-data-attribution'
  reason: 'MAGIC remains peak-LDS first hop; CIGA is surface-form-robust gradient attribution for instruction-data selection'
  use_instead: method:magic
- when: 'output-layer-gradient data selection for SFT/RL (LESSER)'
  reason: 'LESSER cheapens LM-head gradients; CIGA filters layers by surface-form stability'
  use_instead: method:lesser
assumptions:
- 'Instruction-tuning data selection with semantics-preserving paraphrases as a robustness probe. No public code as of 2026-10-28.'
last_reviewed: '2026-10-28'
papers:
- paper:ciga
recipes:
- recipe:ciga
claims:
- benchmark: 'Instruction-data selection under wording/format paraphrases'
  metric: 'attribution stability under semantics-preserving surface-form changes; downstream selection quality'
  value: 'keeps layers whose gradients are both influential and stable under surface-form perturbations, then fuses them so wording/format no longer flips example scores'
  baseline: 'global gradient attribution (LESS-style) without surface-form invariance'
  date: '2026-10-28'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.36755'
  notes: 'Does not retarget method:magic.'
tags:
- data-attribution
- sft
- active
---

# CIGA

## Method Overview
CIGA first keeps layers whose gradients stay stable under semantics-preserving rewrites, then dynamically fuses those features so instruction-data scores track content rather than wording or format.

## When to Use
- Gradient data selection for SFT where paraphrasing an example changes its influence score even though the content is the same.

## When NOT to Use
Default on `task:training-data-attribution` remains `method:magic`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:magic`.

## Gotchas & Failure Modes
- Not a replacement for `method:magic`.
- Paper claims are dated 2026-10-28; no locked-SOTA bake-off.
