---
id: paper:curvdelta
type: paper
title: 'CurvDelta: Low-Curvature Preservation Geometry for Parameter-Efficient Fine-Tuning'
authors:
- Zeguan Xiao
- Zhuocheng Liang
- Yun Chen
- Yong Wang
- Guanhua Chen
- Pinyan Lu
year: 2026
month: 11
arxiv_id: '2611.24654'
url: https://arxiv.org/abs/2611.24654
methods:
- method:curvdelta
cites: []
tags:
- peft
- lora
- kfac
- curvature
- continual
- active
---

# CurvDelta: Low-Curvature Preservation Geometry for Parameter-Efficient Fine-Tuning

## Abstract Summary
CurvDelta / CurvLoRA constrain PEFT updates to a K-FAC low-curvature subspace so sequential tasks overwrite less. Gemma-3-1B math ALL 22.2 vs FT 19.4 / LoRA 17.5. Llama-2-7B math CurvLoRA ALL 40.1 vs Replay 40.2 / FT 33.4; code ALL 42.8 vs LoRA 41.7 / FT 39.6. TOFU SimNPO Llama-3.1-8B CurvLoRA Forget 10% FP 3.4 / MU 62.5 vs Retrain 10.6 / 64.6; CurvDelta FQ 6.5 / MU 63.2. Code xiaozi-max/curvdelta_learning. Does not supersede vanilla LoRA + rsLoRA + LR sweep.

## Key Contributions
1. K-FAC low-curvature preservation for sequential PEFT.
2. CurvDelta (full-delta geometry) and CurvLoRA (LoRA-constrained).
3. Continual math/code plus TOFU unlearning.

## Empirical Highlights
Gemma-3-1B math ALL 22.2 vs FT 19.4 / LoRA 17.5. Llama-2-7B math 40.1 vs Replay 40.2.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.24654`
- Code: `https://github.com/xiaozi-max/curvdelta_learning`
- Unlearning: `https://github.com/xiaozi-max/curvdelta_unlearning`
