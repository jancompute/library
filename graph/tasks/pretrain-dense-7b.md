---
id: task:pretrain-dense-7b
type: task
title: "Pretrain Dense ~7B Language Model from Scratch"
domain: "pretraining"
summary: "Pretraining a dense ~7B parameter transformer language model from scratch targeting maximum token efficiency and loss reduction."
current_sota:
  - method: method:muon2
    as_of: "2026-08-26"
    benchmark: "Moonlight Scaling Laws / FineWeb Token Mix"
    metric: "token efficiency"
    value: "~2x token efficiency vs AdamW"
    notes: "Muon2 (2604.09967) + KL-SOAP (2607.20548) if memory allows."
redirects:
  - when: "shared n-gram tables with layer-wise rescale (Chorus; not the 7B optimizer)"
    to: "method:chorus"
  - when: "Canon layers / local token mixing at 8B (not the 7B optimizer)"
    to: "method:canon-layers"
  - when: "HiSA hidden-dimension RoPE QK sparsity from scratch (not the 7B optimizer)"
    to: "method:hisa-rope"
  - when: "hierarchical cross-layer KV reconstruction as pretrain regularizer (DepthGraft; not the 7B optimizer)"
    to: "method:depthgraft"
  - when: "on-policy mid-training distillation (OPMD-CPT; not the 7B optimizer)"
    to: "method:opmd-cpt"
  - when: "KL-recovery MTP gradient (Soft-MTP), not the 7B optimizer"
    to: "method:soft-mtp"
  - when: "nested sparsity for scalable pretraining and continual learning (NESTOR)"
    to: "method:nestor"
  - when: "unique-token epoch / repetition geometry under a finite pretrain corpus"
    to: "task:data-constrained-pretrain"
  - when: "latent-space / next-concept LM architecture rather than dense NTP 7B"
    to: "task:latent-space-lm-pretrain"
  - when: "fully synthetic single-stage LLM pretraining from Wikipedia/Wikibooks seeds"
    to: "task:synthetic-single-stage-pretrain"
  - when: "zero-natural-data self-play pretraining (UTM programs, no natural text)"
    to: "task:zero-natural-data-self-play-pretrain"
  - when: "Muon-style norm-aware update for embedding tables (1->2) and LM head (2->inf) instead of AdamW"
    to: "method:muonio"
  - when: "one-step prefix-augmented OPD for continued pretrain (PA1-OPD)"
    to: "method:pa1-opd"
methods:
  - method:chorus
  - method:canon-layers
  - method:hisa-rope
  - method:depthgraft
  - method:opmd-cpt
  - method:soft-mtp
  - method:nestor
  - method:pa1-opd
  - method:clean
  - method:dga-muon
  - method:orca
  - method:muon2
  - method:soap-muon-scale
  - method:muon-scalable
  - method:muon
  - method:mona
  - method:htmuon
  - method:variance-adaptive-muon
  - method:sf-normuon
  - method:newton-muon
  - method:nemotron-3-nano
  - method:adamw-optimizer
  - method:qwen38-next
  - method:layer-dropout
  - method:optimizer-memory-schedules
  - method:musec
  - method:ncp-archpreview
  - method:synth
  - method:self-play-pretraining
  - method:muonio
last_reviewed: '2026-11-20'
tags:
  - pretraining
  - dense-lm
  - optimizer
---

# Pretrain Dense ~7B Language Model from Scratch

## Problem Definition
Training a ~7B dense language model from scratch requires optimizing billions of parameters over trillions of tokens with maximal compute and wall-clock efficiency.

## SOTA Recommendation (as of 2026-09-08)
- **Optional shared n-gram tables (not this 7B optimizer)**: `method:chorus` (`arXiv:2611.23386`). 1.2B tables 0.9229 BPB beat 9.6B Engram/FactorEngram; ClimbMix 9.6B 0.9148 vs FactorEngram 0.9258. Code dualverse-ai/chorous. Mention on `task:llm-pretraining-optimization`. Does not replace Muon2.
- **Optional Canon layers (not this 7B optimizer)**: `method:canon-layers` (`arXiv:2611.24963`). Local token mixing; 8B ~30% token save; LlamaCanon 8B/1T lm-eval/MMLU 67.7/62.4 vs Llama 66.9/60.6. Code facebookresearch/PhysicsLM4. Mentions on `task:llm-pretraining-optimization` / `task:linear-time-sequence-modeling`. Does not replace Muon2 or Mamba-2.
- **Optional HiSA RoPE QK sparsity (not this 7B optimizer)**: `method:hisa-rope` (`arXiv:2611.26363`). 135M 4K val 2.880 vs dense 2.906 at 29.3% QK; 16K PG19 3.170 vs 3.205 at 20.2% QK. Code ambroise-b/hisa. Distinct from AF1 HiSA. Mention on `task:posttrain-attention-sparsification`. Does not replace Muon2 or SAS.
- **Related hierarchical KV reconstruction (not this 7B optimizer)**: `method:depthgraft` (`arXiv:2611.03142`) on `task:llm-pretraining-optimization`. Pretrain regularizer, not Muon2. Does not replace Muon2.
- **Related mid-training reverse-KL CPT (not this 7B optimizer)**: `method:opmd-cpt` (`arXiv:2611.13855`) on `task:student-distillation`. Distinct from `method:opmd`. Qwen NTP on MegaMath collapses; OPMD-CPT does not. Does not replace Muon2.
- **Primary Optimizer**: **Muon2** (`method:muon2`, 2604.09967) + **KL-SOAP** (`method:soap-muon-scale`, 2607.20548) if GPU memory allows. Default I/O layers stay AdamW; optional `method:muonio` (`arXiv:2610.02705`) for embedding \(1\to 2\) / LM-head \(2\to\infty\). Unchanged hidden-layer default.
- **Data Recipe**: **OLMo-3 / Dolma-3** (`paper:olmo-3`, 2512.13961).
- **Not this scale**: ~1.5-2B on consumer GPUs / tight budget is `method:puro-2b` (`task:budget-consumer-pretrain`), not this 7B default.
- **Adjacent hybrid residual / Qwen-style production architecture**: `method:qwen38-next`. Does not replace Muon2 as the 7B optimizer.
- **Optional layer sparsity**: `method:layer-dropout` (`arXiv:2609.05275`). Does not replace Muon2.
- **OT-horizon HP guidance**: `method:optimizer-memory-schedules` (`arXiv:2609.04577`). 51M–253M study; do not retarget this 7B optimizer.
- **Optional Muon stability plug-in**: `method:musec` (`arXiv:2609.11655`). Does not replace Muon2.
- **Latent-space LM architecture (not this task)**: `method:ncp-archpreview` on `task:latent-space-lm-pretrain`.
- **Fully synthetic single-stage pretrain (not this 7B web/open NTP)**: `method:synth` on `task:synthetic-single-stage-pretrain`. Baguettotron-600M is 594M on SYNTH, not a 7B Dolma run.
- **Zero-natural-data self-play pretrain (not this task)**: `method:self-play-pretraining` on `task:zero-natural-data-self-play-pretrain`.
