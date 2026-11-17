---
id: paper:polpo
type: paper
title: 'Policy Optimization With Multiple Verifiers via Pareto Rankings'
authors:
- Kai Yamashita
- Shohei Taniguchi
- Hiroki Furuta
- Masahiro Suzuki
- Yutaka Matsuo
year: 2026
month: 11
arxiv_id: '2611.19064'
url: https://arxiv.org/abs/2611.19064
methods:
- method:polpo
cites: []
tags:
- multi-reward
- pareto
- dpo
- active
---

# Policy Optimization With Multiple Verifiers via Pareto Rankings

## Abstract Summary
Multiple verifiers yield partial success that a scalar reward discards or mis-orders. POLPO uses Pareto dominance and maximizes the listwise likelihood of all complete rankings consistent with that partial order. Code generation and instruction following: better learning efficiency and more complete requirement satisfaction than scalar-reward training. Distinct from GPDPO (filtered GRPO reuse) and CorrGRPO/DARA (aggregation). No public code. Does not retarget CorrGRPO / DARA.

## Key Contributions
1. Pareto partial orders over multi-verifier outcomes.
2. Listwise likelihood over all consistent complete rankings (DPO family).
3. Supervision from verified improvements before complete success.

## Empirical Highlights
Improved learning efficiency and higher complete-requirement rates vs scalar aggregation on code and IF.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.19064`
- Code: none found (`code_status: none`).
