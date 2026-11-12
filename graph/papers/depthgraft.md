---
id: paper:depthgraft
type: paper
title: 'DepthGraft: Structural Regularization through Hierarchical Cross-Layer KV Reconstruction'
authors:
- Xiaohan Qin
- Xiangdong Zhang
- Yu Wang
- Huaijin Wu
- Zhuo Xia
- Yebin Yang
- Junchi Yan
year: 2026
month: 11
arxiv_id: '2611.03142'
url: https://arxiv.org/abs/2611.03142
methods:
- method:depthgraft
cites: []
tags:
- pretrain
- kv-cache
- architecture
- active
---

# DepthGraft: Structural Regularization through Hierarchical Cross-Layer KV Reconstruction

## Abstract Summary
Cross-layer KV sharing is a pretrain regularizer, not only a serving cache trick. DepthGraft reconstructs deep-layer KV from stride-aligned shallow–middle pairs, so the gradient path through the cache is a structural prior. Sibling of MSAR (residual topology). Distinct from DeepSeek-V4.1-Flash serving. HF Daily leftover below the 11-11 watermark. Code jianke0604/DepthGraft (same author as MSAR).

## Key Contributions
1. Hierarchical reconstruction of deep KV from shallow–middle pairs during pretrain.
2. Same regularizer on dense and MoE, GQA and MLA, $0.5$B–$16$B.
3. KV cache about one-third smaller as a side effect of the sharing pattern.

## Empirical Highlights
16B MoE MMLU-Pro $+7.0\%$, CMMLU $+6.6\%$, C3 $+6.4\%$. Does not retarget Muon2, DeepSeek-V4, or V4.1-Flash.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.03142`
- Code: `https://github.com/jianke0604/DepthGraft` (`code_status: released`).
