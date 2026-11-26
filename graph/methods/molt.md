---
id: method:molt
type: method
title: MoLT (Mixture-of-Loops Transformer)
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'experimental CED all-token recurrence as the first hop'
    reason: 'RLT remains the experimental CED hop; MoLT is KV-as-memory looping with U-MoLT encoder-decoder readout'
    use_instead: method:recurrent-looped-transformer
  - when: 'elastic mixed-depth looped LM (gated state update / mixed loop counts)'
    reason: 'ELR varies loop count; MoLT reuses KV memory across loops at a trained architecture'
    use_instead: method:elr
  - when: 'compute-matched MoE looping of middle layers (FLOPs/params/KV matched)'
    reason: 'SMELT loops middle MoE layers under a matched budget; MoLT is KV memory plus U-shaped readout'
    use_instead: method:smelt
  - when: 'standard dense ~7B NTP from scratch'
    reason: 'Muon2 remains the ~7B optimizer; MoLT is a looped architecture recipe'
    use_instead: method:muon2
  - when: 'input-heavy agentic / KV-compressed CED serving rather than recurrent LM pretrain'
    reason: 'V4.1-Flash is serving; MoLT is a pretrain architecture'
    use_instead: method:deepseek-v41-flash
assumptions:
  - '400B-token from-scratch U-MoLT vs OLMo3 at 700M/1.5B dense and 3B MoE; 100B-token U-MoLT CPT of Qwen3.5-0.8B-Base. MoLA fused Triton in hustvl/MoLT. U-MoLT is CED-like (memory construction vs prediction readout), not mixed-depth ELR and not SMELT middle-50% twice.'
last_reviewed: '2026-11-26'
papers:
- paper:molt
recipes:
- recipe:molt
claims:
- benchmark: '400B-token U-MoLT vs OLMo3, 700M dense val CE token efficiency'
  metric: 'token-efficiency ratio'
  value: '1.7×'
  baseline: 'OLMo3 matched 700M'
  date: '2026-11-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.34923'
  notes: 'Also 1.5B dense and 3B MoE. 3B MoE 10-domain PPL −0.75 and 10-task +2.1pp. Code hustvl/MoLT. Does not retarget RLT, ELR, SMELT, or Muon2.'
- benchmark: 'Qwen3.5-0.8B-Base 100B-token continued pretrain'
  metric: 'mean token efficiency vs matched baseline'
  value: '1.4×; lower CE on all 11 domains'
  baseline: 'matched non-looped CPT'
  date: '2026-11-26'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.34923'
  notes: 'S-size (~113M) MoL-Hybrid-2 996.6 vs 1,000.6 ms vs non-looped OLMo3.'
tags:
- architecture
- looped-transformer
- kv-memory
- active
---

# MoLT (Mixture-of-Loops Transformer)

## Method Overview
MoLT answers what a Transformer should pass between loops: keys and values. Mixture-of-Loops Attention (MoLA) reuses KV as memory. MoLT-R keeps the residual stream. MoLT-KV restarts from embeddings and mixes current-loop local KV with earlier-loop memory KV, which removes same-position cross-loop dependence and, with loop forcing, allows single-traversal decode past the train horizon. U-MoLT builds memory in an encoder-like pass and reads it for prediction, skipping unused decoder traversals.

## When to Use
- Looped pretrain where the bottleneck is loop-to-loop state, not mixed decode depth or SMELT-style middle-layer visits.

## When NOT to Use
Experimental CED first hop remains `method:recurrent-looped-transformer`. Mixed-depth looping remains `method:elr`. Compute-matched MoE looping remains `method:smelt`. Dense ~7B NTP remains `method:muon2`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:recurrent-encoder-decoder-lm` with mentions on `task:elastic-depth-looped-lm` and `task:compute-matched-moe-looped-pretrain`. Distinct from ELR / SMELT / RLT / Loopback / Concertina. Does **not** replace RLT, ELR, SMELT, or Muon2.

## Gotchas & Failure Modes
- U-MoLT is encoder-decoder readout, not mixed-depth ELR and not SMELT's middle 50% twice.
- MoLT-KV plus loop forcing is required for single-traversal MoL decode beyond the train loop count.
- Latency match is reported at S-size (~113M) with MoL-Hybrid-2, not at 7B.
