---
id: paper:rds-mopd
type: paper
title: 'Robust Domain-Mixture Scheduling for Multi-Teacher On-Policy Distillation'
authors:
- Yankai Chen
- Sida Lin
- Yifan Li
- Hanjun Luo
- Hanrong Zhang
- Zhuohan Xie
- Bowei He
- Wei-Chieh Huang
- Meng Ding
- Wei Xue
- Yike Guo
- Philip S. Yu
- Xue Liu
year: 2026
month: 11
arxiv_id: '2611.12012'
url: https://arxiv.org/abs/2611.12012
methods:
- method:rds-mopd
cites:
- paper:open-mopd
- paper:opd
tags:
- distillation
- mopd
- dro
- active
---

# Robust Domain-Mixture Scheduling for Multi-Teacher On-Policy Distillation

## Abstract Summary
RDS-MOPD keeps a DRO domain-mixture objective for multi-teacher OPD and redesigns the three parts that break under noisy per-domain KL: noise-aware radius calibration, spike-robust allocation, and worst-case as regression from each domain's own best level. On SmolLM3-3B with the Open-MOPD teachers, BO Avg. Rank is $1.50$ vs D$^3$-MOPD $2.58$ / Open-MOPD $2.67$, recovery $118.1\%$ vs $106.5$ / $105.6$. Paper Open-MOPD numbers are not the library $83.4\%$ bake-off. No public code as of 2026-11-10.

## Key Contributions
1. DRO mixture scheduling for MOPD that protects lagging domains rather than the fastest-improving ones.
2. Three modules (NRC / SAE / WDR) with bounded share-change and bounded spike-influence guarantees.
3. Stress test: injected code-teacher noise does not lock the mixture onto the noisy domain.

## Empirical Highlights
BO (mean $\pm$ std, 3 seeds): AIME24/25 $26.72/26.09$ vs D$^3$-MOPD $24.77/24.90$; LCB v5/v6 $23.79/23.01$ vs Open-MOPD $22.46/22.31$; IFEval $74.74$. Does not retarget Open-MOPD.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.12012`
- Code: none found (`code_status: none`).
