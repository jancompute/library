---
id: paper:simplehc
type: paper
title: 'On the Design of Hyper-Connections: Simplification, Stability, and Scalability'
authors:
- Xiangdong Zhang
- Xiaohan Qin
- Sunan Zou
- Tuo Dai
- Bizhao Shi
- Zhuo Xia
- Yebin Yang
- Yizhou Chen
- Yuliang Liu
- Yu Cheng
- Junchi Yan
year: 2026
month: 11
arxiv_id: '2611.05984'
url: https://arxiv.org/abs/2611.05984
methods:
- method:simplehc
cites: []
tags:
- architecture
- hyper-connections
- mhc
- pretraining
- active
---

# On the Design of Hyper-Connections: Simplification, Stability, and Scalability

## Abstract Summary
SimpleHC removes residual mixing and shares memory access in Hyper-Connections. Matches mHC at 15B/30B MoE (loss 1.561, avg 63.1 vs mHC 62.9). Extra train time vs vanilla 2.4% at C=6144 vs mHC ~7.0%. Backward storage −31%. GitHub `aHapBean/SimpleHC` is README plus paper PDF (`code_status: announced`). Hugging Face Daily leftover below the 2611.14515 watermark. Does not retarget mHC or DeepSeek-V4.

## Key Contributions
1. Drop residual mixing; keep learned read/write gating.
2. Shared memory access cuts backward storage.
3. Matches mHC quality at 15B/30B MoE with a smaller train-time tax.

## Empirical Highlights
15B/30B MoE: loss 1.561, avg 63.1 vs mHC 62.9. Train-time overhead 2.4% vs vanilla at C=6144 (mHC ~7.0%). Backward storage −31%. Distinct from MSAR (multi-stream attention residuals).

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.05984`
- Code: `https://github.com/aHapBean/SimpleHC` (`code_status: announced`; README + paper PDF as of 2026-11-13).
