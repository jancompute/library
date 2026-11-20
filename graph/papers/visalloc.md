---
id: paper:visalloc
type: paper
title: 'VisAlloc: Allocating Visual Supervision for On-Policy Self-Distillation'
authors:
- Haoran Xu
- Tian Chen
- Yuhe Wu
- Yanbo Zhao
- Junchi Liao
- Hongyu Wang
- Jiaze Li
- Wentao Wang
- Yanfeng Li
- Rui Qian
year: 2026
month: 11
arxiv_id: '2611.25069'
url: https://arxiv.org/abs/2611.25069
methods:
- method:visalloc
cites: []
tags:
- opsd
- mllm
- visalloc
- privileged-teacher
---

# VisAlloc: Allocating Visual Supervision for On-Policy Self-Distillation

## Abstract Summary
MLLM privileged OPSD with a sample-level paired-teacher filter and token-level counterfactual reweight. Keep examples the positive evidence crop answers correctly and a spatially displaced negative crop answers incorrectly. Token weights come from view sensitivity and teacher disagreement under a conserved inverse-frequency micro-batch budget. The positive teacher is the only distill target; inference uses the full-image student.

## Key Contributions
1. Fixed paired-teacher filter (6,241 → 5,795 pairs).
2. Geometry-matched positive/negative crops plus conserved token-weight budget.
3. Eight-benchmark Qwen3.5-4B/9B bake-off vs reproduced Vision-OPD.

## Empirical Highlights
Macro 81.44 / 84.92 at 4B / 9B vs Vision-OPD 80.47 / 84.40 (+0.97 / +0.52). 9B vs OPD-V +1.56. Filter+JSD ladder: 80.47 → 81.44. MME-RealWorld EN/CN +0.98 each (excluded from the eight-task macro).

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.25069`
- Code: `https://github.com/Kaelyn01/VisAlloc`
