---
id: paper:specopd
type: paper
title: 'SpecOPD: Branch-Parallel On-Policy Distillation for Speculative Decoding'
authors:
- Tianyu Liu
- Jun Zhang
- Wenjie Huang
- Yuhao Shen
- Tianqi Xu
- Xinyue Hao
- Hongyaoxing Gu
- Xuyang Liu
- Baolin Zhang
- Yating Zhu
- Shuang Ge
- Jun Dai
- Lei Chen
- Yue Li
- Mingchen Wan
year: 2026
month: 11
arxiv_id: '2611.02846'
url: https://arxiv.org/abs/2611.02846
methods:
- method:specopd
cites:
- paper:opd
- paper:mdraft
- paper:uno
tags:
- speculative-decoding
- opd
- drafter
- active
---

# SpecOPD: Branch-Parallel On-Policy Distillation for Speculative Decoding

## Abstract Summary
SpecOPD parallelizes draft sampling and target supervision across independent branches at reference anchors, packed into proposal trees. An E2E-TV surrogate targets acceptance length. Distinct from sequential Draft-OPD rollouts and from MDraft.

## Key Contributions
1. Branch-parallel OPD that does not inherit draft-and-verify serialization.
2. Up to +41.45% mean AL and 16.09× supervised-token throughput vs sequential OPD; 3.56× vs AR.

## Empirical Highlights
8B / 27B / 125B targets; DFlash / DSpark / DFlash V2. Does not retarget Uno or OPD.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.02846`
- Code: none found (`code_status: none`). Related prior art: `https://github.com/Simplified-Reasoning/Draft-OPD`.
