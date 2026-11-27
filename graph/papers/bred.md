---
id: paper:bred
type: paper
title: 'BReD: Block Replay Dithering for Stable Low-Bit EMA Optimizer States'
authors:
- Heshen Zhan
- Youhan Huang
- Yunke Peng
- Yao Wang
- Linghui Kong
- Ziwei Zhu
- Qingyu Han
- Yaoyuan Wang
- Congliang Chen
- Ruoyu Sun
year: 2026
month: 11
arxiv_id: '2611.33951'
url: https://arxiv.org/abs/2611.33951
methods:
- method:bred
cites:
- paper:zip-sr
- paper:scale
- paper:muon2
tags:
- optimizer
- quantization
- ema
- active
---

# BReD: Block Replay Dithering for Stable Low-Bit EMA Optimizer States

## Abstract Summary
Low-bit optimizer-state storage is not one-shot quant: EMA states are dequantized, updated, and requantized every step, so rounding bias and variance recurse as \(e_{t+1}=\beta e_t+\epsilon_{t+1}\). BReD applies subtractive dithering with deterministic seed replay and one shared dither per block, so no auxiliary random tensor is stored. Leaves the host optimizer update and HPs unchanged. Distinct from ZIP-SR (AdamW second-moment codebook + preconditioner-space SR) and from SCALE subspace projections.

## Key Contributions
1. Identifies EMA error accumulation as the failure mode of iterative low-bit optimizer-state storage.
2. Block Replay Dithering: subtractive dither + seed replay + block-shared values.
3. 4-bit BReD matches full-precision PPL within 0.5 (pretrain) / 0.2 (FT); 3-bit still converges in the paper's settings.

## Empirical Highlights
Five optimizers at 120M; AdamW and Muon at 1.1B and 3.4B pretrain; AdamW and Muon FT at 7B. 4-bit PPL shift \(\le 0.5\) pretrain / \(\le 0.2\) FT; downstream within 0.7. Nearest / stochastic rounding under the same grid can diverge. Code ZhanHeshen/BReD.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.33951`
- Code: `https://github.com/ZhanHeshen/BReD`
