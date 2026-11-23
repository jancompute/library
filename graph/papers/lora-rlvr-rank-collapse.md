---
id: paper:lora-rlvr-rank-collapse
type: paper
title: 'Structure Over Scale: Rethinking Adaptation for Reinforcement Learning with Verifiable Rewards'
authors:
- Allan Kazakov
- Abdurrahman Javat
year: 2026
month: 11
arxiv_id: '2611.27148'
url: https://arxiv.org/abs/2611.27148
methods:
- method:lr-matters-lora
- method:cispo
cites: []
tags:
- lora
- rlvr
- peft
- rank-collapse
---

# Structure Over Scale: Rethinking Adaptation for Reinforcement Learning with Verifiable Rewards

## Abstract Summary
Claim note, no new method. Under a common cold-start GRPO protocol, vanilla LoRA is stable at low rank then collapses as rank grows. Qwen3-8B DeepMath-Hard (seed 42, batch 64, G=8) is 73.1% at \(r=64\) then 4.7% at \(r=128\) and 2.3% at \(r=256\). Raising batch size does not rescue high rank. Do not revive DoRA as the 24GB quality default.

## Key Contributions
1. Documents LoRA rank collapse under cold-start GRPO.
2. Shows larger batch size can move the collapse boundary downward.
3. Spectral evidence that structured adapters keep a wider effective-rank region.

## Empirical Highlights
Qwen3-8B DeepMath-Hard \(r=64\) 73.1% → \(r=128\) 4.7% / \(r=256\) 2.3%. Batch 128/256 collapses \(r=64\) to 8.7%/6.0%.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.27148`
- Code: `https://github.com/Shrimpstanot/structure-over-scale`
