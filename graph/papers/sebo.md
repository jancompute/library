---
id: paper:sebo
type: paper
title: 'See Every Block Once: Variance-Reduced Post-Training for Masked Diffusion Language Models'
authors:
- Yunzhen He
- Hiroaki Yamagiwa
- Hidetoshi Shimodaira
year: 2026
month: 11
arxiv_id: '2611.17754'
url: https://arxiv.org/abs/2611.17754
venue: AACL-IJCNLP 2026
methods:
- method:sebo
cites: []
tags:
- dllm
- elbo
- post-training
- active
---

# See Every Block Once: Variance-Reduced Post-Training for Masked Diffusion Language Models

## Abstract Summary
SEBO is a full-block unbiased ELBO estimator for masked dLLM post-train: evaluate every block once instead of random block sampling. LLaDA-8B-Instruct +12.79 avg vs SPG; highest on 4/5 of GSM8K, MATH-500, Countdown, Sudoku, HumanEval. AACL-IJCNLP 2026. GitHub githubhyz/See_Every_Block_Once empty. Does not retarget A2D / JustOPD / ForkGRPO.

## Key Contributions
1. Random-block ELBO is high-variance; full-block once is unbiased and lower-variance.
2. Same MDLM objective; the change is the estimator.
3. Peer-reviewed AACL-IJCNLP 2026.

## Empirical Highlights
GSM8K 82.26, MATH-500 38.00, Sudoku 91.39 vs SPG 72.73, HumanEval 36.59. +12.79 avg vs random block.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.17754`
- Code: `https://github.com/githubhyz/See_Every_Block_Once` (`code_status: announced`; empty as of 2026-11-16).
