---
id: paper:dram
type: paper
title: 'DRAM: Memory-Efficient Muon via Rank Reallocation in Principal-Random Subspaces'
authors:
- Haomin Bai
- Dingzhi Yu
- Xuling Zhao
- Sifan Yang
- Yibo Wang
- Lijun Zhang
year: 2026
month: 11
arxiv_id: '2611.28595'
url: https://arxiv.org/abs/2611.28595
methods:
- method:dram
cites: []
tags:
- optimizer
- muon
- memory-efficient
- subspace
---

# DRAM: Memory-Efficient Muon via Rank Reallocation in Principal-Random Subspaces

## Abstract Summary
DRAM keeps Muon momentum and matrix-sign normalization inside a compact principal-random subspace. Rank starts principal-heavy and reallocates linearly toward random coverage. Stochastic \(O(T^{-1/4})\) and deterministic \(O(T^{-1/2})\) rates hold for nondecreasing coverage schedules. Distinct from SCALE / PMRC / GaLore-Muon. No public code.

## Key Contributions
1. Principal-random subspace: TopSVD directions plus random directions from the orthogonal complement.
2. Stage-wise rank reallocation from \((k-1,1)\) to \((0,k)\) while staying in the subspace.
3. Best low-memory downstream at 60M/130M/350M C4 pretrain and 8/9 full-parameter FT settings.

## Empirical Highlights
LLaMA-60/130/350M C4 avg 36.28 / 37.19 / 38.55 vs best other low-memory 35.98 / 37.11 / 38.45. Peak GPU mem vs Full-Muon 19.6–20.7% (Qwen3-8B 52.80→42.47 GiB). Nine FT settings 17.9–20.7% mem cut.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.28595`
- Code: none found as of 2026-11-24
