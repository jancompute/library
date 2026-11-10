---
id: paper:agentic-opd
type: paper
title: 'Agentic-OPD: Recovering Forgotten Agent Capabilities via On-Policy Distillation for Agentic Tasks'
authors:
- Tingcheng Bian
- Kangye Gong
- Jinchang Luo
- MingQuan Cheng
- Feiran Liu
- Ni Li
- Xiaoling Xia
- Haiwei Wang
- Hui Li
year: 2026
month: 11
arxiv_id: '2611.12799'
url: https://arxiv.org/abs/2611.12799
methods:
- method:agentic-opd
cites:
- paper:opd
- paper:open-mopd
tags:
- distillation
- opd
- agentic
- checkpoint-mining
- active
---

# Agentic-OPD

## Abstract Summary
Agentic-OPD reuses discarded GRPO checkpoints as a latent teacher library. Hierarchical Checkpoint Navigation (HCN) plus Layer-wise Adaptive Distillation (LAD) pick which checkpoint to query and which layers to match. DeepSearch mean vs GRPO $+2.8/+7.4/+2.6$ on Qwen2.5-3B/7B and Qwen3-4B. Qwen3-4B Agentic-OPD $50.4$ vs GRPO $47.8$ vs GPT-5.6 $25.4$ / DeepSeek-V4.1 $42.7$ on their DeepSearch protocol (not a harness ranking). No public code as of 2026-11-10.

## Key Contributions
1. Treat discarded RL checkpoints as an implicit expert library rather than trash.
2. HCN: token-level trajectory entropy plus KL-to-init for teacher selection.
3. LAD: per-layer teacher choice plus adaptive weight; skip layers that would regress.

## Empirical Highlights
DeepSearch mean 3B $47.3$ vs GRPO $44.5$; 7B $54.4$ vs $47.0$; 4B $50.4$ vs $47.8$. GAIA/HLE/xbench-DeepSearch also listed. Does not retarget OPD, Open-MOPD, or CANOPY.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.12799`
- Code: none found (`code_status: none`).
