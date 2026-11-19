---
id: method:flashmorph2
type: method
title: FlashMorph2
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'post-train gated sparse attention under a fixed per-query budget'
    reason: 'SAS remains gated post-train first hop; FlashMorph2 selects which layers keep full attention'
    use_instead: method:sas
  - when: 'linear-time architecture from scratch (SSM / Mamba)'
    reason: 'Mamba-2 is from-scratch linear-time; FlashMorph2 converts a pretrained Transformer'
    use_instead: method:mamba-2
  - when: 'hybrid residual / Qwen-style next architecture from scratch'
    reason: 'Qwen3.8-Next is a production hybrid recipe; FlashMorph2 is Transformer-to-hybrid conversion'
    use_instead: method:qwen38-next
assumptions:
  - 'Pretrained dense Transformer. Discrete hybrid mask with K full-attention layers; remaining layers linear (GLA / GDN / Lightning). Paper: Qwen3-0.6B/1.7B/8B and Qwen3-30B-A3B. No public v2 GitHub as of 2026-11-19.'
last_reviewed: '2026-11-19'
papers:
- paper:flashmorph2
recipes:
- recipe:flashmorph2
claims:
- benchmark: 'Qwen3 0.6B/1.7B × GLA/GDN/Lightning vs FlashMorph (avg)'
  metric: 'RULER / LongBench avg'
  value: 'RULER 63.26→65.68 (+2.42); LongBench 29.86→30.94 (+1.08); recall +0.76'
  baseline: 'FlashMorph'
  date: '2026-11-19'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.24809'
  notes: 'Does not retarget method:sas / method:mamba-2. code_status none.'
- benchmark: 'Layer-selection cost Qwen3 0.6B–8B'
  metric: 'GPU hours'
  value: '0.72–3.57 GPU-h; 8.4–20.8× vs HALO; 560–854× vs KL-LS'
  baseline: 'HALO / KL-LS'
  date: '2026-11-19'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.24809'
  notes: 'Selection is <1% of conversion token budget. Does not retarget SAS.'
tags:
- hybrid-attention
- layer-selection
- on-policy
- post-training
- active
---

# FlashMorph2

## Method Overview
FlashMorph2 selects which layers of a pretrained Transformer keep full attention under a K-layer budget by sampling discrete hybrid architectures end to end and jointly adapting weights under the recovery objective.

## When to Use
- Convert a dense pretrained LM to hybrid full+linear attention when FlashMorph's continuous teacher-forced gates mismatch deployed discrete hybrids.

## When NOT to Use
Gated per-query sparse attention remains `method:sas`. From-scratch linear-time remains `method:mamba-2`. Production hybrid-from-scratch remains `method:qwen38-next`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:posttrain-attention-sparsification`. Mention on `task:linear-time-sequence-modeling`. Does **not** replace SAS.

## Gotchas & Failure Modes
- Off-policy computation ablation drops RULER by 29.55 (all full-attn layers piled at the bottom).
- No public v2 repo (`code_status: none`).
