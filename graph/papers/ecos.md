---
id: paper:ecos
type: paper
title: 'ECOS: Environment-Calibrated On-Policy Self-Distillation for Language Agents'
authors:
- Chenhao Zhang
- Zhongan Wang
- Mingxuan Li
- Hehe Fan
- Zheng Zhu
- Ming Li
year: 2026
month: 11
arxiv_id: '2611.12232'
url: https://arxiv.org/abs/2611.12232
methods:
- method:ecos
cites:
- paper:opd
tags:
- distillation
- opsd
- agentic
- environment-calibration
- active
---

# ECOS

## Abstract Summary
ECOS is environment-calibrated OPSD for LLM agents. The teacher sees only the executable command plus a one-token environment-calibration suffix; it never sees the full privileged response. 3B/7B ALFWorld seen $90.5/93.3$, WebShop $75.5/80.5$; unseen ALFWorld $+11.0/+7.6$ vs GRPO. 3B WebShop command-only teacher $75.0$ vs full-response $52.3$. No public code as of 2026-11-10.

## Key Contributions
1. Command-only privileged teacher plus a one-token environment-calibration suffix.
2. Avoids full-response teacher traces that collapse agent OPSD.
3. Seen/unseen ALFWorld and WebShop on Qwen2.5-3B/7B.

## Empirical Highlights
Unseen ALFWorld 3B/7B $+11.0/+7.6$ vs GRPO. Command-only vs full-response is the load-bearing ablation. Does not retarget CANOPY or VISTA.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.12232`
- Code: none found (`code_status: none`).
