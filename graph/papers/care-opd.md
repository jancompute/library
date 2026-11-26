---
id: paper:care-opd
type: paper
title: 'CARE-OPD: Confidence-Aware Replay for Efficient On-Policy Distillation in Agentic Training'
authors:
- Haowen Hou
- Gen Li
- Ruilin Li
- Yicheng Liu
- Zhen Huang
- Shuai Dong
- Congcong Wang
- Kaiwen Tuo
- Hongrui Wu
- Zelin Peng
- Kanghui Tian
- Ji Zhao
- Dianyi Wang
- Jiaqi Wang
year: 2026
month: 11
arxiv_id: '2611.34756'
url: https://arxiv.org/abs/2611.34756
methods:
- method:care-opd
cites: []
tags:
- distillation
- opd
- agentic
---

# CARE-OPD: Confidence-Aware Replay for Efficient On-Policy Distillation in Agentic Training

## Abstract Summary
CARE-OPD replaces live teacher rollouts on agent trajectories with student-seeded teacher completions from a prefix replay buffer, gated by teacher-student confidence, then allocated by hindsight return. Distinct from SWE-OPD (offline cached teacher), PivotOPD (pivotal-mistake reverse/forward KL), State-OPD (matched interaction state), ECOD (experience-calibrated teacher weights), and `method:care-po` (tool-budget RL).

## Key Contributions
1. Prefix-replay OPD: teacher completes student-seeded prefixes instead of rolling out the full trajectory.
2. Confidence gating plus hindsight replay allocation.
3. SWE-bench Verified agentic bake-off vs async online OPD.

## Empirical Highlights
SWE-bench Verified 59.5% vs async online OPD. End-to-end time −45%. Environment actions −44%. No public GitHub as of 2026-11-26.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.34756`
- Code: none found as of 2026-11-26
