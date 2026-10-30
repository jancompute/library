---
id: paper:c-mopd
type: paper
title: 'Turing LLM Post-Training: Calibrated Distillation and Efficient Dynamic-MoE Execution'
authors:
- 'Yue He'
- 'Jiahui Hu'
- 'Shaman Tang'
- 'Hua Zhou'
- 'Qiman Wu'
- 'Menglin Li'
- 'Yizhao Wang'
- 'Yuheng Zhang'
- 'Da Zhu'
- 'Zhou Wang'
- 'Anhua Liu'
- 'Hanlin Chen'
- 'Mingyuan Wang'
- 'Rui Xin'
- 'Yuhua Wei'
- 'Shuang Su'
- 'Siqi Liu'
- 'Kai Yang'
- 'Weichao Huang'
- 'Hang Zhang'
- 'Honggou Yang'
- 'Xianming Liu'
year: 2026
month: 10
arxiv_id: '2610.39876'
url: https://arxiv.org/abs/2610.39876
methods:
- method:c-mopd
cites:
- paper:open-mopd
tags:
- mopd
- moe
- active
---

# Turing LLM Post-Training: Calibrated Distillation and Efficient Dynamic-MoE Execution

## Abstract Summary
C-MOPD matches each selected teacher on a local Top-K support with teacher-wise loss normalization and clipping so independently optimized specialists can be merged into a dynamic-MoE student. The paper also describes an execution path; this card is the distillation.

## Key Contributions
1. Calibrated multi-teacher OPD for dynamic MoE specialist integration.

## Empirical Highlights
Turing-20B-A2B four-domain normalized integration 0.9988; retains >=90.16% of specialist gain in every domain. Matched K=32: full calibration 0.9962 vs 0.9724 without calibration vs 0.9834 without clipping. Does not retarget method:open-mopd. Execution/serving path is out of graph scope.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.39876`
- Code: `none found (`code_status: none`).`
