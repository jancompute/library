---
id: paper:levenshtein-edit-dlm
type: paper
title: 'LED: A Framework of Levenshtein Editing for Diffusion Language Models'
authors:
- Shuaidi Wang
- Zhuocheng Gong
- Xuejie Liu
- Jianguo Li
- Yu Zhang
year: 2026
month: 11
arxiv_id: '2611.23750'
url: https://arxiv.org/abs/2611.23750
methods:
- method:levenshtein-edit-dlm
cites: []
tags:
- dllm
- levenshtein
- insert-delete
- post-training
- active
---

# LED: A Framework of Levenshtein Editing for Diffusion Language Models

## Abstract Summary
Levenshtein Editing (paper LED; library slug `levenshtein-edit-dlm`) post-trains masked diffusion LMs with insert and delete operations, not only remask. On LLaDA2.1-Mini 16B: conf-guided 54.86→57.10; conf-free 27.52→47.19; block 128 36.97→51.34. Distinct from `method:led` (lookahead-edit SFT, 2610.23122). Code inclusionAI/LLaDA2.X (LLaDA2.2 release). Does not retarget A2D.

## Key Contributions
1. Insert/delete as first-class dLLM post-train operations.
2. Confidence-guided and confidence-free edit schedules.
3. Gains at larger decode blocks (block 128).

## Empirical Highlights
LLaDA2.1-Mini 16B conf-guided 54.86→57.10 / conf-free 27.52→47.19; block 128 36.97→51.34.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.23750`
- Code: `https://github.com/inclusionAI/LLaDA2.X`
