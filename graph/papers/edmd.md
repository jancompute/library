---
id: paper:edmd
type: paper
title: 'eDMD: Endpoint Distribution Matching for Few-Step Diffusion Distillation'
authors:
- Tong Zhao
- Xianfang Zeng
- Yucheng Han
- Ruoyu Wang
- Mingkun Lei
- Gang Yu
- Chi Zhang
year: 2026
month: 11
arxiv_id: '2611.17194'
url: https://arxiv.org/abs/2611.17194
methods:
- method:edmd
cites: []
tags:
- diffusion
- dmd
- few-step
- active
---

# eDMD: Endpoint Distribution Matching for Few-Step Diffusion Distillation

## Abstract Summary
eDMD trains the fake score only on the student's final outputs, with a precise teacher (short multi-step on the final noise interval) and calibrated query density. 4-step distill of SD3-Medium, FLUX.2-klein 4B/9B, Qwen-Image-2.1. Highest peak HPSv3++ vs DMD2/TDM/D-DMD/CDM. No real images. Code Westlake-AGI-Lab/eDMD. Does not retarget DiffusionOPSD / Self-OPD.

## Key Contributions
1. Endpoint-only fake-score DMD instead of full-trajectory matching.
2. Precise teacher via short multi-step on the final noise interval.
3. No real images; 4-step students of SD3 / FLUX.2-klein / Qwen-Image.

## Empirical Highlights
SD3-M peak HPSv3++ 11.171 vs D-DMD 10.841; FLUX.2-klein-4B 12.699 vs DMD2 11.337; FLUX.2-klein-9B 12.431 vs D-DMD 11.325. Held-out lead +0.30 / +1.37 / +1.11 / +0.47. Qwen-Image peak 14.69 vs backprop-only 13.60.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.17194`
- Code: `https://github.com/Westlake-AGI-Lab/eDMD` (`code_status: released`).
