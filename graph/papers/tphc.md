---
id: paper:tphc
type: paper
title: 'TPHC: Improving Hyper-Connections with Tensor-Parallel Grouped Updates'
authors:
- Xinying Hu
- You Wu
- Haoyi Wu
- Jianchao Tan
- Kefeng Zhang
- Yuchen Xie
- Kewei Tu
year: 2026
month: 11
arxiv_id: '2611.23026'
url: https://arxiv.org/abs/2611.23026
methods:
- method:tphc
cites: []
tags:
- architecture
- hyper-connections
- mhc
- tensor-parallel
- pretraining
- active
---

# TPHC: Improving Hyper-Connections with Tensor-Parallel Grouped Updates

## Abstract Summary
TPHC groups Hyper-Connection residual streams for tensor-parallel updates instead of replicating the full mix. On 1.1B models trained for 100B SlimPajama tokens, TPHC4 val 2.0838 / avg 48.9 vs mHC4 2.0985 / 48.6; TPHC8 2.0706 / 49.3 vs mHC8 2.0924 / 48.8; TPHC8 beats mHC16 (2.0885 / 49.0). 8B TP-sharded TPHC4 is +9% train time vs mHC4. Code wuyou2002/TPHC. Does not retarget mHC, SimpleHC, or DeepSeek-V4.

## Key Contributions
1. Tensor-parallel grouped Hyper-Connection updates instead of a fully replicated mix.
2. Sparse per-group write plus initialization that keeps residual diversity.
3. Sharded streams keep expansion from N=4 to 16 at +19% vs +59% replicated.

## Empirical Highlights
1.1B / 100B SlimPajama: TPHC4 2.0838/48.9 vs mHC4 2.0985/48.6; TPHC8 2.0706/49.3 vs mHC8 2.0924/48.8 and vs mHC16 2.0885/49.0. 8B TP-sharded TPHC4 +9% train time vs mHC4.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.23026`
- Code: `https://github.com/wuyou2002/TPHC` (`code_status: released`; size 48 as of 2026-11-18).
