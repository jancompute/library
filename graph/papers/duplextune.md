---
id: paper:duplextune
type: paper
title: 'DuplexTune: Coupled-State Replay for Memory-Efficient Mixture-of-Experts Adaptation'
authors:
- 'Paul Raj'
- 'Simon Caldwell'
- 'Daniel Whitmore'
- 'Mutlu Mete'
year: 2026
month: 10
arxiv_id: '2610.36009'
url: https://arxiv.org/abs/2610.36009
methods:
- method:duplextune
cites:
- paper:scale
tags:
- peft
- moe
- memory
- active
---

# DuplexTune: Coupled-State Replay for Memory-Efficient Mixture-of-Experts Adaptation

## Abstract Summary
Sparse expert execution does not remove stored states needed to adapt an MoE. DuplexTune replays coupled residual streams through pretrained modules with width bridges and a frozen router.

## Key Contributions
1. DuplexTune as an active MoE coupled-state memory plug-in on task:full-param-memory-efficient-pretrain.

## Empirical Highlights
Qwen1.5-MoE-A2.7B 38.8 vs 64.8 GB and 25.1 vs 19.9 samples/s vs checkpointed SFT. Weaker multilingual. Does not retarget method:scale.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.36009`
- Code: `none found (`code_status: none`).`
