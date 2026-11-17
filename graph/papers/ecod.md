---
id: paper:ecod
type: paper
title: 'ECOD: Experience-Calibrated On-Policy Distillation for Multi-Turn Agents'
authors:
- Jie Jin
- Shengqin Wang
- Yan Gao
- Xin Tan
- Yuan Xie
year: 2026
month: 11
arxiv_id: '2611.18656'
url: https://arxiv.org/abs/2611.18656
methods:
- method:ecod
cites: []
tags:
- opd
- multi-turn
- agent
- active
---

# ECOD: Experience-Calibrated On-Policy Distillation for Multi-Turn Agents

## Abstract Summary
ECOD weights teacher losses or teacher-derived advantages from student-teacher trajectory comparison plus a temporal prior from successful teacher lengths. Qwen2.5-1.5B/7B-Instruct on ALFWorld and WebShop. Up to +4.06% relative ALFWorld unseen vs OPD. Across SOD / TCOD-F2B / ATOD, average paired +6.20% ALFWorld unseen / +7.05% WebShop (WebShop 2.29%–21.60%). No public code. Does not retarget CANOPY / OPD.

## Key Contributions
1. Experience-calibrated weights on teacher losses or advantages.
2. Temporal prior from successful teacher lengths.
3. Reusable across several distill objectives (SOD, TCOD-F2B, ATOD).

## Empirical Highlights
+4.06% relative ALFWorld unseen vs OPD. Average paired +6.20% / +7.05% across both scales.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.18656`
- Code: none found (`code_status: none`).
