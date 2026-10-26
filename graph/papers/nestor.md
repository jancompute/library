---
id: paper:nestor
type: paper
title: 'Nested Sparsity for Scalable Pretraining and Continual Learning'
authors:
- 'Tianzhe Chu'
- 'Druv Pai'
- 'Yi Ma'
year: 2026
month: 10
arxiv_id: '2610.31818'
url: https://arxiv.org/abs/2610.31818
methods:
- method:nestor
cites:
- paper:muon2
- paper:deepseek-v4
tags:
- architecture
- sparsity
- active
---

# Nested Sparsity for Scalable Pretraining and Continual Learning

## Abstract Summary
MoE transformers sparsify the FFN. NESTOR studies nested sparsity as another conditional-compute axis for scalable pretraining and continual learning.

## Key Contributions
1. NESTOR as an active plug-in on task:pretrain-dense-7b.

## Empirical Highlights
- Nested sparsity vs MoE-FFN conditional compute. Does not retarget method:muon2 or method:deepseek-v4.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.31818`
- Code: `https://github.com/Ma-Lab-Berkeley/Nestor` (`code_status: released`).
