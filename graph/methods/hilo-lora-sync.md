---
id: method:hilo-lora-sync
type: method
title: 'HiLo (LoRA Sync)'
category: training-systems
status: active
sota_for: []
supersedes: []
do_not_use_for:
  - when: 'choosing the production frontier RL post-train engine'
    reason: 'Miles remains the engine; HiLo is LoRA gradient-replay sync over a bandwidth-limited uplink'
    use_instead: method:miles
  - when: 'bit-exact delta-compressed weight sync / refit for disaggregated agentic RL (NeMo-DCR)'
    reason: 'NeMo-DCR ships changed full-weight coordinates; HiLo compresses LoRA-factor gradients and replays the optimizer'
    use_instead: method:nemo-dcr
  - when: 'cross-budget self-distillation for masked dLLMs (HiLo-RD)'
    reason: 'HiLo-RD is a dLLM representation-matching method; this HiLo is LoRA synchronization'
    use_instead: method:hilo-rd
  - when: 'low-rank gradient sketches + predicted-KL step control for RL memory'
    reason: 'LoGRA sketches trainer gradients for memory; HiLo compresses the learner-to-worker LoRA sync path'
    use_instead: method:logra
assumptions:
  - 'Disaggregated LoRA on-policy post-training (OPD / RLAD / GRPO-family) where rollout workers can hold replicated optimizer state. Paper: Qwen3-1.7B / 0.6B rank-64 LoRA. Distinct from method:hilo-rd (arXiv 2610.36901). No public code as of 2026-11-12. arXiv 2611.13306 is a Wednesday leftover above the 11-11 ingest watermark.'
last_reviewed: '2026-11-12'
papers:
- paper:hilo-lora-sync
recipes:
- recipe:hilo-lora-sync
claims:
- benchmark: 'KK OPD Qwen3-1.7B / Countdown-4 RLAD Qwen3-0.6B, rank-64 LoRA, 1.6% payload'
  metric: 'pass@4 vs full adapter sync / end-to-end step speedup'
  value: 'KK 81.6 vs full sync 83.2; Countdown-4 63.7 vs 64.0; up to 2.2× E2E on bandwidth-limited links'
  baseline: 'full rank-64 adapter sync / Delta post-optimizer compression / low-rank LoRA r=k'
  date: '2026-11-12'
  verified: true
  evidence_level: preprint
  source_url: 'https://arxiv.org/abs/2611.13306'
  notes: 'Does not retarget method:miles or method:nemo-dcr. Distinct from method:hilo-rd. Workers must match optimizer implementation and replay messages in order.'
tags:
- lora
- systems
- opd
- rlvr
- active
---

# HiLo (LoRA Sync)

## Method Overview
HiLo (high-rank in training, low-rank on the wire) replaces LoRA adapter broadcast with compressed LoRA-factor gradient messages. Learner and rollout workers start from the same parameters and optimizer state, decode the same wire message, and apply the same optimizer transition, so they stay at the same policy version. Spar is the LoRA-specific backend: Gram-matrix spectral truncation, global rank allocation under a byte budget, and error feedback. Training rank stays high; communication rank is a budget.

## When to Use
- Distributed on-policy LoRA (OPD / RLVR / RLAD) over a bandwidth-constrained learner-to-worker path, when workers can hold optimizer state.

## When NOT to Use
The production engine remains `method:miles`. Bit-exact full-weight delta sync remains `method:nemo-dcr`. Masked-dLLM HiLo-RD remains `method:hilo-rd`. Trainer-side gradient sketches remain `method:logra`.

## Relation to Existing SOTA
Active plug-in (`sota_for: []`) on `task:frontier-rl-posttrain-stack`. Does **not** replace Miles or NeMo-DCR. Distinct from `method:hilo-rd`.

## Gotchas & Failure Modes
- Replay needs matching optimizer code, state precision, and in-order versioned messages. Bitwise equality is stricter than same-version consistency.
- Does not remove temporal staleness; it only removes learner–worker same-version discrepancy.
- LoRA updates are dense; lossless full-weight delta codecs are the wrong family.
- No public code as of 2026-11-12.
