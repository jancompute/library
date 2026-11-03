---
id: paper:sonar-moe
type: paper
title: 'Sonar-MoE: In-Backward Expert Updates for Memory-Efficient Mixture-of-Experts Training'
authors:
- 'Avni Mittal'
- 'Avinash Anand'
- 'Ashutosh Kumar'
- 'Dikshant Kukreja'
- 'Kritarth Prasad'
- 'Chaitanya Lakhchaura'
- 'Rishitej Reddy Vyalla'
- 'Erik Cambria'
- 'Zhengkui Wang'
- 'Rajiv Ratn Shah'
year: 2026
month: 11
arxiv_id: '2611.03577'
url: https://arxiv.org/abs/2611.03577
methods:
- method:sonar-moe
cites:
- paper:scale
- paper:duplextune
tags:
- moe
- memory
- active
---

# Sonar-MoE: In-Backward Expert Updates for Memory-Efficient Mixture-of-Experts Training

## Abstract Summary
MoE training keeps every expert gradient until the optimizer step. Sonar-MoE updates each expert tensor during backward and frees its gradient, so the GPU never holds more than one layer of expert gradients. Updates are bitwise-identical to standard training without expert clipping.

## Key Contributions
1. In-backward expert updates for MoE, one layer of expert gradients at a time.

## Empirical Highlights
OLMoE-1B-7B and Granite-3.1-3B-A800M bf16: 19-22% peak memory cut; held-out loss within 0.003; 17-23% faster than global-norm clipping. Updating whole batched tensors avoids a 20-72% slowdown vs per-expert in-backward.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.03577`
- Code: none found (`code_status: none`).
