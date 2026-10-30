---
id: paper:a-rsi
type: paper
title: 'A-RSI: Adaptive Task Refresh for Zero-Data Multimodal Self-Improvement'
authors:
- 'Yu Liu'
- 'Youxing Li'
- 'Yuedong Tan'
- 'Zhiwei Yang'
- 'Zihan Su'
- 'Hanqi Feng'
- 'Shaojie Zhang'
- 'Libin Liao'
- 'Zihao Wan'
- 'Chenxu Wu'
- 'Cong Cao'
- 'Fangfang Yuan'
- 'Yanbing Liu'
- 'Ziheng Chen'
- 'Pei Fu'
- 'Radu Timofte'
- 'Zongwei Wu'
- 'Nicu Sebe'
- 'Barnabas Poczos'
- 'Jian Luan'
year: 2026
month: 10
arxiv_id: '2610.38568'
url: https://arxiv.org/abs/2610.38568
methods:
- method:a-rsi
cites:
- paper:j-zero
tags:
- rsi
- multimodal
- active
---

# A-RSI: Adaptive Task Refresh for Zero-Data Multimodal Self-Improvement

## Abstract Summary
A-RSI watches reward variation and accuracy in training logs and refreshes the task pool when the learning signal declines, without looking at val/test. A static library of model-authored programs writes multimodal questions with independently checkable answers, so supervision is not majority vote.

## Key Contributions
1. When-to-refresh zero-data multimodal RSI, not Challenger-Solver-Judge.

## Empirical Highlights
Project seerray-lab.github.io/A-RSI/. Does not retarget method:j-zero.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.38568`
- Code: `project `https://seerray-lab.github.io/A-RSI/` (`code_status: none`).`
