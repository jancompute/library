---
id: method:simplex-lora
type: method
title: 'SimplexLoRA'
category: peft
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:lora-quality-tuning'
  reason: 'Vanilla LoRA + rsLoRA + LR sweep remains the 24GB quality default; SimplexLoRA reallocates a frozen parameter budget across adapter ranks'
  use_instead: method:lr-matters-lora
- when: 'memory must fit a 4-bit PEFT stack'
  reason: 'AQLoRA-Q remains 4-bit PEFT; SimplexLoRA is full-precision rank allocation'
  use_instead: method:aqlora-q
assumptions:
- 'Short simplex warm-up then frozen importance weights. DeBERTaV3, BART-large, Llama 3.1 8B, Qwen3-8B. EMNLP 2026 Findings. Code: brain-lab-research/SimplexLoRA.'
last_reviewed: '2026-10-28'
papers:
- paper:simplex-lora
recipes:
- recipe:simplex-lora
claims:
- benchmark: '12 language understanding, summarization, and reasoning tasks on DeBERTaV3 / BART-large / Llama 3.1 8B / Qwen3-8B'
  metric: 'task score vs LoRA and adaptive-rank baselines at matched parameter budget'
  value: 'matches or outperforms standard LoRA and recent adaptive baselines, with the largest gains at low ranks'
  baseline: 'fixed-rank LoRA; recent adaptive-rank LoRA'
  date: '2026-10-28'
  verified: true
  evidence_level: peer-reviewed
  source_url: 'https://arxiv.org/abs/2610.37206'
  notes: 'Does not retarget method:lr-matters-lora.'
tags:
- peft
- lora
- active
---

# SimplexLoRA

## Method Overview
SimplexLoRA learns per-adapter importance weights on an n-scaled simplex during a short warm-up, freezes them, and reallocates rank under a fixed parameter and inference budget.

## When to Use
- LoRA quality tuning where a uniform rank wastes budget on some layers and you can spend a short warm-up to reallocate it.

## When NOT to Use
Default on `task:lora-quality-tuning` remains `method:lr-matters-lora`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:lr-matters-lora`.

## Gotchas & Failure Modes
- Not a replacement for `method:lr-matters-lora`.
- Paper claims are dated 2026-10-28; no locked-SOTA bake-off.
