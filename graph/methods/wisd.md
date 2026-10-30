---
id: method:wisd
type: method
title: 'WISD'
category: distillation
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:teacher-free-on-policy-self-adaptation'
  reason: 'OPSA remains entropy-adaptive negative advantages; WISD contrasts a quantized/pruned weaker self'
  use_instead: method:opsa
- when: 'a gold reference solution is available for privileged OPSD'
  reason: 'VISTA remains privileged-teacher OPSD; WISD uses no privileged context'
  use_instead: method:vista
assumptions:
- 'Unlabeled prompts. Quantized or pruned shadow of the same checkpoint. Official code jet-ai-projects/WISD.'
last_reviewed: '2026-10-30'
papers:
- paper:wisd
recipes:
- recipe:wisd
claims:
- benchmark: 'math/code reasoning vs original checkpoints (HMMT 2025 / LiveCodeBench v6)'
  metric: 'accuracy'
  value: 'prune Qwen3.5-4B 57.7→70.5 HMMT / 39.1→56.7 LCB; quant Qwen3.6-35B-A3B 68.5→74.6 / 61.8→69.5; avg +4.0/+5.5'
  baseline: 'original model; privileged OPSD'
  date: '2026-10-30'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2610.38681'
  notes: 'Does not retarget method:opsa.'
tags:
- opsd
- teacher-free
- active
---

# WISD

## Method Overview
WISD constructs a weaker counterpart of the current policy (INT-low quantization or magnitude prune) and distills the original toward the contrast with that weaker self on unlabeled prompts. No gold solution, no external teacher.

## When to Use
- Teacher-free / unlabeled-prompt self-adaptation when you can afford a quantized or pruned shadow copy.

## When NOT to Use
OPSA remains the locked first hop on `task:teacher-free-on-policy-self-adaptation`. Privileged gold OPSD remains VISTA.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:opsa` or `method:vista`.

## Gotchas & Failure Modes
- Paper claims are dated 2026-10-30; no locked-SOTA bake-off.
- Needs a weaker clone; not a drop-in for entropy-only OPSA.
