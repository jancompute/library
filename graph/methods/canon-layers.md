---
id: method:canon-layers
type: method
title: Canon Layers
category: architecture
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'choosing the ~7B dense pretrain optimizer'
    reason: 'Muon2 remains the optimizer; Canon is local token mixing on every sublayer'
    use_instead: method:muon2
  - when: 'linear-time architecture from scratch (SSM / Mamba)'
    reason: 'Mamba-2 remains the linear-time hop; Canon is a cheap mix that can make GLA match GDN/Mamba2'
    use_instead: method:mamba-2
  - when: 'hybrid residual / Qwen-style next architecture from scratch'
    reason: 'Qwen3.8-Next is the production hybrid recipe; Canon is PhysicsLM mixing'
    use_instead: method:qwen38-next
  - when: 'shared n-gram tables with layer-wise rescale (Chorus; not Canon mix)'
    reason: 'Chorus is n-gram tables; Canon is neighbor mixing inside each sublayer'
    use_instead: method:chorus
assumptions:
  - 'From-scratch Llama / GLA / GDN / Mamba2 at 1.3B–8B on 1–2T Nemotron-CC. Canon <0.2% params. Strict alignment adds an MLP and halves Mamba2 depth. Code facebookresearch/PhysicsLM4 as of 2026-11-20.'
last_reviewed: '2026-11-20'
papers:
- paper:canon-layers
recipes:
- recipe:canon-layers
claims:
- benchmark: 'Llama 8B / 1T Nemotron-CC'
  metric: 'lm-eval(13) / MMLU'
  value: 'LlamaCanon 67.7 / 62.4 vs Llama 66.9 / 60.6; ~30% tokens for same 8B MMLU; matches Llama-3.1-8B at 1/15 tokens'
  baseline: 'vanilla Llama (same data/budget); Llama-3.1-8B token count'
  date: '2026-11-20'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.24963'
  notes: 'Does not retarget method:muon2. Vanilla 8B Llama +2.5 vs Nvidia Transformer on the same data.'
- benchmark: 'Strictly aligned linear models 8B / 1T'
  metric: 'lm-eval(13) / MMLU'
  value: 'GLA5+Canon 68.0 / 63.0 vs Mamba2 67.3 / 61.6 vs GDN2+Canon 68.2 / 64.0'
  baseline: 'strictly aligned Mamba2 / GDN2'
  date: '2026-11-20'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.24963'
  notes: 'With Canon, GLA5 matches GDN2 and beats Mamba2. Linear models still fail 500-token retrieval. Does not retarget method:mamba-2.'
tags:
- architecture
- pretrain
- canon
- gla
- active
---

# Canon Layers

## Method Overview
Canon layers mix neighboring tokens inside every Transformer or recurrent sublayer at under 0.2% extra parameters. GLA5 and GDN2 replace full-rank output gates with rank-16 factorizations and give the saved parameters back to the rest of the layer. Strict alignment equalizes parameter split, recurrent memory, and heads across GLA, GDN, and Mamba2.

## When to Use
- From-scratch dense or linear pretrain when you can add cheap horizontal mixing and want ~30% fewer tokens for the same 8B MMLU.

## When NOT to Use
Optimizer choice remains `method:muon2`. Linear-time default remains `method:mamba-2`. Production hybrid-from-scratch remains `method:qwen38-next`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:pretrain-dense-7b`. Mentions on `task:llm-pretraining-optimization` and `task:linear-time-sequence-modeling`. Does **not** replace Muon2 or Mamba-2.

## Gotchas & Failure Modes
- Academic-scale 1.3B/100B can hide architecture gaps after LR tuning; the paper's claim is 1–2T.
- Strictly aligned Mamba2 adds an MLP and halves depth versus the original Mamba-2 recipe.
- Matching lm-eval does not imply 500-token retrieval or two-hop questions.
