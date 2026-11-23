---
id: paper:cmhc
type: paper
title: 'cmHC: Balancing Stream Mixing in Hyper-Connections via Geometric Contraction'
authors:
- Haowei He
- Ziwen Zhao
- Chenshuo Pan
- Gang Lin
- Zhihao Yang
- Chao Wang
- Xinzhang Liu
- Kaidong Yu
- Han Gao
- Dongfang Li
- Menglin Yang
- Shuangyong Song
- Yongxiang Li
year: 2026
month: 11
arxiv_id: '2611.27193'
url: https://arxiv.org/abs/2611.27193
methods:
- method:cmhc
cites: []
tags:
- architecture
- hyper-connections
- pretraining
- moe
---

# cmHC: Balancing Stream Mixing in Hyper-Connections via Geometric Contraction

## Abstract Summary
mHC residual matrices cluster near permutation vertices. cmHC contracts permutation bases toward the Birkhoff interior, \(\tilde{P}=\lambda P+(1-\lambda)11^{\top}/n\), with \(\lambda=0.97\) on the first \(K=2\) layers and no new parameters. Distinct from mHC Sinkhorn, SimpleHC, and TPHC.

## Key Contributions
1. Geometric contraction of Birkhoff permutation bases without new parameters.
2. Shallow-only moderate contraction to bound over-mixing.
3. Dense nanoGPT and 6B/300B-MoE pretrain plus fused Ascend kernels.

## Empirical Highlights
OpenWebText vs mHC-lite −0.0073/−0.0024/−0.0045 S/M/L. 6B-MoE at 71.5k −0.002 vs mHC / −0.005 vs mHC-lite. 300B-MoE −0.0157 vs mHC at 2k (early). Ascend latency −44.8%.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.27193`
- Code: `https://github.com/Newiz430/cmHC`
