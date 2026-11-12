---
id: paper:hilo-lora-sync
type: paper
title: 'Train High, Ship Low: Efficient LoRA Synchronization for Distributed On-Policy Post-Training'
authors:
- Shenghui Li
- Li Ju
- Thiemo Voigt
year: 2026
month: 11
arxiv_id: '2611.13306'
url: https://arxiv.org/abs/2611.13306
methods:
- method:hilo-lora-sync
cites: []
tags:
- lora
- systems
- opd
- rlvr
- active
---

# Train High, Ship Low: Efficient LoRA Synchronization for Distributed On-Policy Post-Training

## Abstract Summary
Distributed on-policy LoRA post-training bottlenecks on adapter broadcast. HiLo ships compressed LoRA-factor gradients and has each rollout worker replay the optimizer locally, so learner and workers stay at the same policy version. Spar is a budget-aware spectral compressor (Gram eigendecomposition, adaptive rank, error feedback) that decouples training rank from wire bytes. Distinct from `method:hilo-rd` (masked dLLM representation matching). No public code as of 2026-11-12.

## Key Contributions
1. Compressor-agnostic optimizer-replay protocol; same decoded gradient on learner and workers.
2. Spar: spectral truncation of LoRA-factor gradients under a global byte budget.
3. Same-version consistency is separate from temporal staleness.

## Empirical Highlights
HiLo+Spar at $1.6\%$ of rank-64 adapter bytes: KK OPD Qwen3-1.7B pass@4 $81.6$ vs full sync $83.2$; Countdown-4 RLAD Qwen3-0.6B $63.7$ vs $64.0$. Up to $2.2\times$ end-to-end on bandwidth-limited links. Distinct from NeMo-DCR (bit-exact full-weight delta). Does not retarget Miles.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.13306`
- Code: none found (`code_status: none`).
