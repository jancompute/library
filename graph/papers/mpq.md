---
id: paper:mpq
type: paper
title: 'MPQ: A Message-Passing View of Post-Training Quantization'
authors:
- 'Yanshuo Chen'
- 'Chenxi Liu'
- 'Reza Shirkavand'
- 'Heng Huang'
year: 2026
month: 10
arxiv_id: '2610.32127'
url: https://arxiv.org/abs/2610.32127
methods:
- method:mpq
cites:
- paper:gradcodes
tags:
- quantization
- ptq
- active
---

# MPQ

## Abstract Summary
GPTQ-family PTQ commits each block before neighbors are considered. MPQ keeps alternate codewords alive with message passing.

## Key Contributions
1. MPQ as an active plug-in on task:full-lowbit-finetune.

## Empirical Highlights
- Delayed-commit PTQ vs GPTQ. Does not retarget method:gradcodes.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.32127`
- Code: `https://github.com/poseidonchan/MPQ` (`code_status: released`).
