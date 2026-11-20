---
id: paper:shadow-posterior-matching
type: paper
title: 'Reinforcing Few-Step Diffusion Models via Shadow Posterior Matching'
authors:
- Jingqiao Xiu
- Yicong Li
year: 2026
month: 11
arxiv_id: '2611.25998'
url: https://arxiv.org/abs/2611.25998
methods:
- method:shadow-posterior-matching
cites: []
tags:
- diffusion
- few-step
- rl
- posterior-matching
---

# Reinforcing Few-Step Diffusion Models via Shadow Posterior Matching

## Abstract Summary
Few-step generators are samplers, not score models, so multi-step RL credit either blurs samples, skips the final call, or exploits a fitted proxy. Shadow Posterior Matching (SPM) renoises generated samples into shadow inputs, takes black-box reward credit from the non-degenerate shadow posterior, and adds a teacher-anchor plus endpoint-matching regression. Distinct from FewStepRL (average-velocity host port) and eDMD (endpoint fake-score DMD). Slug is `shadow-posterior-matching` because `method:bpo` already occupies PMD.

## Key Contributions
1. Shadow credit from measured rewards that reaches every call, including the deterministic final step.
2. Teacher KL on sample distributions plus endpoint matching so shadow inputs match deployed inputs.
3. 4-step SD3.5-Medium bake-off vs RTDMD / TDM-R1 on GenEval, OCR, and PickScore.

## Empirical Highlights
4-step SD3.5-M: GenEval 0.94 / OCR 0.96 / PickScore 23.84 vs strongest 4-step baseline 0.86 / 0.95 / 23.36. Best on 10 of 15 DrawBench quality pairs among 4-step methods. α=γ=0.1, LoRA rank 32, 1,000 steps, 8×H100.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.25998`
- Code: `https://github.com/shadow-posterior/code`
