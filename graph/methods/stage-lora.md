---
id: method:stage-lora
type: method
title: 'Stage-LoRA (SFT/RL Spectral Updates)'
category: peft
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked 24GB LoRA quality default'
  reason: 'Quality default remains vanilla LoRA + rsLoRA + LR sweep; Stage-LoRA is a spectral update plug-in'
  use_instead: method:lr-matters-lora
- when: 'Kronecker PEFT with quadratic rank (SaMA)'
  reason: 'SaMA changes the adapter; Stage-LoRA changes the SFT vs RL update geometry'
  use_instead: method:sama
- when: 'memory must fit a 4-bit PEFT stack'
  reason: '4-bit default remains AQLoRA-Q'
  use_instead: method:aqlora-q
assumptions:
- 'LoRA on math SFT then GRPO. Spectral flatten M preserves Frobenius norm. No public code as of 2026-11-06. arXiv 2611.08414 above watermark 2611.06911.'
last_reviewed: '2026-11-06'
papers:
- paper:stage-lora
recipes:
- recipe:stage-lora
claims:
- benchmark: 'GSM8K Llama-3.2-1B / 3B LoRA, Table 1'
  metric: 'mean test accuracy vs Adam/Adam'
  value: 'SFT M(SGD) 22.82 / 45.72; RL M_perp(Adam) 10.00 / 47.66'
  baseline: 'Adam/Adam SFT 22.24 / 42.99; RL 7.61 / 42.36'
  date: '2026-11-06'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.08414'
  notes: 'Does not supersede method:lr-matters-lora. Group-mean baseline subtraction is the SFT/RL split.'
tags:
- peft
- lora
- active
---

# Stage-LoRA (SFT/RL Spectral Updates)

## Method Overview
Track the singular spectrum and subspaces of LoRA $\Delta W$ separately in SFT and GRPO. SFT expands the spectrum; RL concentrates it because group-mean baseline subtraction tilts the update toward noise-dominated spectral collapse. Apply a norm-preserving flatten $\mathcal{M}$ to the full $B$ direction with an SGD base in SFT, and only to the component of the Adam $B$ direction orthogonal to the current column space of $B$ in RL.

## When to Use
- Same LoRA adapter trained through SFT then GRPO, when a shared Adam setting underfits one of the two stages.

## When NOT to Use
Quality default remains `method:lr-matters-lora`. This is not a new adapter family.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** supersede vanilla LoRA + rsLoRA + LR sweep. Mention on `task:parameter-efficient-fine-tuning`.

## Gotchas & Failure Modes
- Flattening the full Adam $B$ update in SFT can lose to SGD-base $\mathcal{M}$.
- RL flatten must keep the in-subspace Adam component; full $\mathcal{M}(\mathrm{Adam})$ is weaker on Table 1.
