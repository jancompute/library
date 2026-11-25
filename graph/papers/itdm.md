---
id: paper:itdm
type: paper
title: Reinforcing Diffusion Models by Instantaneous Trajectory Distribution Matching
authors:
- Yihong Luo
year: 2026
month: 11
arxiv_id: '2611.30986'
url: https://arxiv.org/abs/2611.30986
methods:
- method:itdm
cites: []
tags:
- diffusion
- rl
- flow-matching
---

# Reinforcing Diffusion Models by Instantaneous Trajectory Distribution Matching

## Abstract Summary
Forward diffusion RL is signed RWR of the policy velocity onto behavior rollouts. That assumes \(v_\theta=v_q\), which fails under CFG and off-policy updates. iTDM is the infinitesimal TDM limit: a sample-level gradient anchored at the behavior velocity, tracked by an auxiliary denoiser. HF Daily leftover below the prior listing watermark.

## Key Contributions
1. Instantaneous TDM gradient with exact baseline invariance at the auxiliary optimum.
2. Online auxiliary denoiser for the behavior velocity.
3. SD3.5-M GenEval2 and FLUX.3 5.6B.

## Empirical Highlights
GenEval2 ~3× faster, scales smoothly to 0.87 without collapse. FLUX.3 5.6B guidance-free HPSv3++ improves in-domain and unseen scores vs competing forward RL.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.30986`
- Code: `https://github.com/Luo-Yihong/iTDM`
