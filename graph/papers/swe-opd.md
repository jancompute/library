---
id: paper:swe-opd
type: paper
title: 'SWE-OPD: On-Policy Distillation for Agentic Coding'
authors:
- Yuhang He
- Yanyu Chen
- Chuanzhe Guo
- Jie Zhu
- Zichen Tian
- Hongyu Ge
- Zixuan Ren
- Huang He
- Bingjin Chen
- Junyuan Shang
- Shuohuan Wang
- Yongqi Zhang
- Irwin King
- Jing Liu
year: 2026
month: 11
arxiv_id: '2611.21020'
url: https://arxiv.org/abs/2611.21020
methods:
- method:swe-opd
cites: []
tags:
- opd
- swe
- agent
- active
---

# SWE-OPD: On-Policy Distillation for Agentic Coding

## Abstract Summary
OPD for agentic coding. Qwen3.5-9B from Qwen3.6-27B: SWE-bench Pro 35.9→39.4. Offline cached teacher 59.4–72.6% fewer GPU-h and ~half peak GPU. Cross-tokenizer GLM-4.5-Air from DeepSeek-V4-Flash-0731: Pro 35.8→39.7 / Multilingual 41.8→46.2. Decreasing top-K reverse-KL can still cause severe repetition (support-mass gradient). Code ernie-research/SWE-OPD. Does not retarget OPD / Cross-Tokenizer OPD / mini-SWE-agent.

## Key Contributions
1. Offline cached teacher for SWE OPD (GPU-hour and peak-GPU cut).
2. Cross-tokenizer transfer on SWE-bench Pro / Multilingual.
3. Decreasing loss ≠ better: top-K reverse-KL repetition via support-mass gradient.

## Empirical Highlights
35.9→39.4 Pro (Qwen3.5-9B). 59.4–72.6% fewer GPU-h. GLM-4.5-Air +3.9 / +4.4 pp.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.21020`
- Code: `https://github.com/ernie-research/SWE-OPD` (`code_status: released`).
