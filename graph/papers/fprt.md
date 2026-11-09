---
id: paper:fprt
type: paper
title: 'FPRT: Failure Profiling and Reachable Trajectory Construction'
authors:
- Yijun Zhu
- Jianxin Wang
- Chengchao Shen
year: 2026
month: 11
arxiv_id: '2611.09042'
url: https://arxiv.org/abs/2611.09042
methods:
- method:fprt
cites:
- paper:opd
- paper:projected-distillation
tags:
- distillation
- sft
- data
- active
---

# FPRT: Failure Profiling and Reachable Trajectory Construction

## Abstract Summary
FPRT is SFT data construction, not OPD matching. It profiles student errors as stubborn / inconsistent / sporadic, then scores teacher corrections by branching-point reachability so the student can actually follow the repair. Llama-3.1-8B / DeepSeek-Math-7B five-bench avg $79.7$ / $80.6$ vs LEMMA $+2.4$ / $+1.8$. NeurIPS 2026. Code: `visresearch/FPRT`. Distinct from projected-distillation.

## Key Contributions
1. Behavioral failure-mode profiling instead of a single correction recipe.
2. Branching-point reachability so the first-error boundary is a trajectory the student can enter.
3. Two construction passes over MetaMathQA; $88.90$K examples matched to LEMMA's budget.

## Empirical Highlights
Table 2 five-bench averages. Trails LEMMA on MATH; lead is concentrated on OOD benches (MAWPS). Does not retarget OPD.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.09042`
- Code: `https://github.com/visresearch/FPRT` (`code_status: released`).
