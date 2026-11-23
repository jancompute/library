---
id: paper:state-kl-opd
type: paper
title: 'When Students Fail to Learn from Teachers: Learning Dynamics of On-Policy Distillation'
authors:
- Xinnan Zhang
- Zeyi Liao
- Siliang Zeng
- Zhongruo Wang
- Jiaxiang Li
- Xinyan Zhao
- Huan Sun
- Mingyi Hong
year: 2026
month: 11
arxiv_id: '2611.27125'
url: https://arxiv.org/abs/2611.27125
methods:
- method:state-kl-opd
cites: []
tags:
- opd
- distillation
- kl-routing
- learning-dynamics
---

# When Students Fail to Learn from Teachers: Learning Dynamics of On-Policy Distillation

## Abstract Summary
Sampled-token reverse-KL OPD can leave mismatch uncorrected where student coverage of the teacher top-\(p\) set is low. State-dependent routing uses forward KL in those states (\(p=0.9\), \(K=16\), \(\varepsilon_1=6\), \(\varepsilon_2=0.3\), \(\varepsilon_3=0.2\)). Distinct from Cal-OPD, OPD-EOS, and AOPD.

## Key Contributions
1. Diagnoses sampled-token OPD failure at low student coverage of the teacher top-p set.
2. State-dependent forward/reverse KL routing with three coverage/underestimation thresholds.
3. Qwen3 1.7B/4B/8B math and code bake-off vs sampled-token OPD.

## Empirical Highlights
Base math Avg@8 +2.36/+2.50/+1.72, Best@8 +2.60/+4.26/+6.24. SFT init +2.08/+1.38/+1.59 Avg@8. Code Avg@8 +2.92/+3.19/+3.44; LiveCodeBench +6.00/+10.93/+8.14.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.27125`
- Code: `https://github.com/zhangxinnan123/learning-dynamic-opd`
