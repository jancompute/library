---
id: paper:rpeg
type: paper
title: 'RPEG: RLM Pipeline Execution Graph'
authors:
- Maciej Besta
- Leonard Schmidt
- Pierre Pang
- Patrik Okanovic
- Robert Gerstenberger
- Torsten Hoefler
year: 2026
month: 11
arxiv_id: '2611.09207'
url: https://arxiv.org/abs/2611.09207
methods:
- method:rpeg
cites:
- paper:miles
tags:
- systems
- rl
- post-training
- active
---

# RPEG: RLM Pipeline Execution Graph

## Abstract Summary
RPEG is a data-centric graph IR plus runtime for RLM PPO/GRPO pipelines. It jointly searches pipeline structure (bounded asynchrony, actor–critic sharing) and execution (stage fusion, scheduling, multi-dimensional parallelism) under an analytical cost model. Up to $2\times$ vs ReaL; up to $2.477\times$ lower step time vs verl (median $1.488\times$) on Llama 3.1 8B / 3.3 70B with separate actor and critic; accuracy within $0.47\%$ of verl. No public code as of 2026-11-09.

## Key Contributions
1. Graph IR that exposes structural and execution choices in one plan.
2. Joint analytical model of compute, communication, memory, and rack/node/GPU hierarchy.
3. Distributed execution up to $256$ GH200 GPUs with utilization $+30\%$.

## Empirical Highlights
A100 vs ReaL $1.4\times$–$2\times$; GH200 vs verl $1.024\times$–$2.477\times$. Does not retarget Miles as the production engine.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.09207`
- Code: none found (`code_status: none`).
