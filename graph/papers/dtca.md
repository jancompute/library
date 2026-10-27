---
id: paper:dtca
type: paper
title: 'DTCA: Denoising Token Credit Assignment for Reinforcement Learning in Diffusion Language Models'
authors:
- 'Hongze Chen'
- 'Miao Pan'
- 'Lizhou Liang'
- 'Qinfeng Li'
- 'Xinyin Ma'
- 'Yongliang Shen'
- 'Weishi Wang'
- 'Daniel Dahlmeier'
- 'Xuhong Zhang'
- 'Wenqi Zhang'
year: 2026
month: 10
arxiv_id: '2610.35201'
url: https://arxiv.org/abs/2610.35201
methods:
- method:dtca
cites:
- paper:forkgrpo
- paper:a2d
tags:
- diffusion
- rlvr
- active
---

# DTCA: Denoising Token Credit Assignment for Reinforcement Learning in Diffusion Language Models

## Abstract Summary
dLLM RL has weak token credit because the reward arrives after many denoising steps. DTCA weights tokens by how much committing them raises confidence on remaining masks, grouped by POS, then calibrates by entropy change.

## Key Contributions
1. DTCA as an active plug-in on task:diffusion-lm-ar-delta-recycle.

## Empirical Highlights
LLaDA-8B-Instruct MATH500 up to +9.0 and GSM8K +5.3 over the base model. Does not retarget method:a2d or method:forkgrpo.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.35201`
- Code: `none found (`code_status: none`).`
