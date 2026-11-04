---
id: method:groupclip
type: method
title: 'GroupClip'
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
- when: 'the locked first hop on task:linear-time-sequence-modeling'
  reason: 'Mamba-2 remains the architecture hop; GroupClip is an embedding-clip stabilizer'
  use_instead: method:mamba-2
assumptions:
- 'Gated sequence models with untied embeddings. GateFloor lives on this card, not a separate method. No public code as of 2026-11-04.'
last_reviewed: '2026-11-04'
papers:
- paper:groupclip
recipes:
- recipe:groupclip
claims:
- benchmark: 'untied gated checkpoints / Nemotron-3-Nano-4B Telugu CPT'
  metric: 'stall rate / steps with zeroed batch grads'
  value: '52.6% of 38 untied gated ckpts stall; FP32 clip overflow zeros grads ~20% of steps'
  baseline: 'tied embeddings / standard FP32 clip'
  date: '2026-11-04'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.04449'
  notes: 'Does not retarget method:mamba-2. GateFloor is the from-scratch companion, not a separate node.'
tags:
- architecture
- ssm
- active
---

# GroupClip

## Method Overview
GroupClip clips embeddings independently of the rest of the model so gated SSMs do not stall at near-zero untied tables. GateFloor (SiLU(z)+δ) is the from-scratch companion on this card.

## When to Use
- Training or CPT of Mamba / GDN / xLSTM with untied embeddings that collapse toward zero.

## When NOT to Use
Mamba-2 remains the linear-time architecture hop. This is a numeric stabilizer, not a new SSM.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`). Does **not** replace `method:mamba-2`.

## Gotchas & Failure Modes
- GateFloor is not a separate library method.
- No public code as of 2026-11-04.
