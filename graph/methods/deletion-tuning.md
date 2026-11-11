---
id: method:deletion-tuning
type: method
title: 'Deletion Tuning'
category: peft
status: active
sota_for: []
supersedes: []
do_not_use_for:
    - when: '24GB quality LoRA / rsLoRA + LR sweep'
      reason: 'Vanilla LoRA + rsLoRA remains the quality default; Deletion Tuning zeros a gate-projection mask'
      use_instead: method:lr-matters-lora
    - when: 'memory must fit a 4-bit PEFT stack'
      reason: 'AQLoRA-Q remains 4-bit PEFT; Deletion Tuning is a sparse mask on full-precision weights'
      use_instead: method:aqlora-q
    - when: 'nested sparsity for scalable pretraining and continual learning'
      reason: 'NESTOR is pretrain/CL nested sparsity; Deletion Tuning is post-train gate-projection deletion'
      use_instead: method:nestor
assumptions:
    - 'Learns a binary mask over transformer gate projections; kept weights stay at pretrained values. Code agentic-learning-ai-lab/deleting-weights released. Hugging Face Daily leftover 2026-11-10; arXiv 2611.10866. Llama-3-8B GSM8K GRPO / Qwen up to 30B-A3B.'
last_reviewed: '2026-11-11'
papers:
- paper:deletion-tuning
recipes:
- recipe:deletion-tuning
claims:
- benchmark: 'Llama-3-8B-Instruct GSM8K GRPO / Qwen2.5-7B SimpleRL-Zoo mean'
  metric: 'accuracy vs full FT'
  value: 'Llama8B GSM8K 83.55 vs FFT 83.24 (8.4 MB mask vs 30633 MB); Qwen7B 52.32 vs 51.89; prior-task drop 0 vs FFT/LoRA/MTH up to 5.4'
  baseline: 'full fine-tune / LoRA r=1,4 / MTH 99%/99.95%'
  date: '2026-11-11'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.10866'
  notes: 'Does not retarget method:lr-matters-lora. Deletes <0.05% of all weights. Also matches FFT under SFT and SDFT. Hugging Face Daily leftover from 2026-11-10.'
tags:
- peft
- sparsity
- deletion
- continual-learning
- active
---

# Deletion Tuning

## Method Overview
Deletion Tuning learns which gate-projection weights to set to zero and writes no new values. A sigmoid over trainable logits hardens into a binary mask. Llama-3-8B-Instruct GSM8K GRPO $83.55$ vs full FT $83.24$ after deleting $<0.05\%$ of weights; the packed mask is $8.4$ MB vs a $30$ GB FFT checkpoint. Prior-task accuracy stays near the base while FFT, LoRA, and random sparse FT drop up to $5.4$ points.

## When to Use
- Post-train (GRPO / SFT / OPD) where an adapter must stay tiny and forgetting of prior tasks is costly.

## When NOT to Use
Quality LoRA remains `method:lr-matters-lora`. 4-bit PEFT remains `method:aqlora-q`. Pretrain nested sparsity remains `method:nestor`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:lora-quality-tuning`. Mentions on `task:parameter-efficient-fine-tuning` and `task:agent-continual-learning`. Does **not** supersede vanilla LoRA + rsLoRA + LR sweep.

## Gotchas & Failure Modes
- Mask is over gate projections only; this is not unstructured prune-anywhere.
- Sequential skills still need a merge policy (not READ-LoRA composition).
- Sibling of NESTOR / Stage-LoRA, not a replacement.
