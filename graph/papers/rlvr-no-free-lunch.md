---
id: paper:rlvr-no-free-lunch
type: paper
title: 'There Is No Free Lunch in RLVR: Every pass@1 Gain Has a pass@k Price'
authors:
- 'Yinuo Liu'
year: 2026
month: 10
arxiv_id: '2610.39295'
url: https://arxiv.org/abs/2610.39295
methods:
- method:cispo
- method:es-reasoning
cites:
- paper:minimax-m1
- paper:sharpening-tax
tags:
- rlvr
- gotcha
---

# There Is No Free Lunch in RLVR: Every pass@1 Gain Has a pass@k Price

## Abstract Summary
RLVR that raises pass@1 strictly lowers some prompt's success under exclusive specialization (Stiemke). When the hardest prompts lose, a pass@k crossover is forced; removing the crossover costs the entire pass@1 gain. The same tilt identity yields entropy collapse. Code yliusci/no-free-lunch-rlvr.

## Key Contributions
1. Exact pass@1 vs pass@k price theorem for RLVR; not a CISPO/ES replacement.

## Empirical Highlights
Constrained updates trace the pass@1 vs pass@k frontier. Complements paper:sharpening-tax. Does not retarget CISPO or ES-reasoning.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.39295`
- Code: `https://github.com/yliusci/no-free-lunch-rlvr (`code_status: released`).`
