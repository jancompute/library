---
id: paper:opsd4mas
type: paper
title: 'Turning Multi-Agent Communication into Token-Level Credit with On Policy Self Distillation'
authors:
- Zixu Wang
- Yu Zhao
- Xing Zheng
- Bingbing Xu
- Tian Xueyun
- JiaTang Luo
- Weiqiang Wang
- Bowen Song
- Huawei Shen
- Xueqi Cheng
year: 2026
month: 11
arxiv_id: '2611.16206'
url: https://arxiv.org/abs/2611.16206
methods:
- method:opsd4mas
cites: []
tags:
- distillation
- opsd
- multi-agent
- grpo
- active
---

# Turning Multi-Agent Communication into Token-Level Credit with On Policy Self Distillation

## Abstract Summary
OPSD4MAS converts future multi-agent communication into token-level OPSD credit: fact extract, association, leave-one-out filter, then an annealed joint with GRPO. MATH pass@4 up to +20.00 vs GRPO; mean pass@1 +8.87 vs GRPO / +6.14 vs DAPO (FW4, six benches). Code `Camel-Prince/OPSD4MAS` (`code_status: released`, verl). Does not retarget OPD or single-agent-plus-tools.

## Key Contributions
1. Communication traces become privileged teacher context for on-policy self-distillation, not a scalar team reward.
2. Fact extract + association + LOO filter drop uninformative messages before the token update.
3. Annealed joint with GRPO so the OPSD term does not replace the outcome signal.

## Empirical Highlights
MATH pass@4 up to +20.00 vs GRPO. Mean pass@1 +8.87 vs GRPO / +6.14 vs DAPO on FW4 six-bench. Distinct from `method:multiagent-opd` (Leader-Searcher-Answerer hierarchical OPD).

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.16206`
- Code: `https://github.com/Camel-Prince/OPSD4MAS` (`code_status: released`; verl).
