---
id: paper:stable-gdn-2
type: paper
title: 'Stable Gated DeltaNet-2: Understanding and Mitigating Recurrent State Instability'
authors:
- Xichong Zhang
- Xixuan Hao
- Zhichen Liu
- Le Zhou
- Zeyu Zhang
- Boyu Chen
- Mingfei Lu
- Zehao Lin
- Bo Tang
- Yonggang Zhang
- Linyun Liu
- Feiyu Xiong
- Jianlin Su
- Zhiyu Li
year: 2026
month: 11
arxiv_id: '2611.34051'
url: https://arxiv.org/abs/2611.34051
methods:
- method:stable-gdn-2
cites:
- paper:gated-deltanet-2
- paper:gga-pw
- paper:pace
tags:
- linear-attention
- gated-deltanet
- stability
- active
---

# Stable Gated DeltaNet-2: Understanding and Mitigating Recurrent State Instability

## Abstract Summary
GDN-2's asymmetric erase operator is non-normal: directional gains accumulate across tokens and the recurrent state can explode even after writes stop. Stable GDN-2 uses symmetric erasure (non-expansive under key-norm / gate constraints) plus a decay-regulated residual write. \(O(\sqrt{T})\) state-growth bound; chunkwise parallel. Distinct from the library's GDN-2 architecture stub (`method:gated-deltanet-2`, arXiv 2605.22791) and from GGA-PW / PACE state quant.

## Key Contributions
1. Traces GDN-2 long-context training failures to asymmetric erasure, not write magnitude.
2. Symmetric erase plus decay-regulated residual write; retains channel-wise gating and chunkwise parallel form.
3. 1.6B recurrent / hybrid 64K pretrain: RULER 128K +6.80 recurrent; nine-task hybrid +0.62 vs GDN-2.

## Empirical Highlights
1.6B models, 64K-context pretrain. Recurrent RULER 128K average +6.80 vs GDN-2. Hybrid nine-task average +0.62. Runs that finish with finite loss can still hold state entries \(>10^{36}\). No public train code as of 2026-11-27 (paper cites NVlabs/GatedDeltaNet-2 for original GDN-2).

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.34051`
- Code: `none found (`code_status: none`).`
