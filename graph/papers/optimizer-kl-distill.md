---
id: paper:optimizer-kl-distill
type: paper
title: 'Do Pretraining Optimizer Gains Transfer to KL Distillation?'
authors:
- Lavinia Ghita
- Dhruv Desai
year: 2026
month: 11
arxiv_id: '2611.19419'
url: https://arxiv.org/abs/2611.19419
methods:
- method:muon2
cites: []
tags:
- muon
- distillation
- gotcha
- active
---

# Do Pretraining Optimizer Gains Transfer to KL Distillation?

## Abstract Summary
Claim note, no trainer. Matrix-structured pretrain optimizer gains (SOAP, Shampoo reductions, All-2D Muon) do not transfer automatically to short-horizon forward-KL distillation from an instruction-tuned init. Four dense Qwen student-teacher pairs. AdamW generally attains the lowest validation KL; AdaGrad can be slightly faster at larger scale; SOAP tracks AdamW in KL at substantial trainer-time overhead; the two Shampoo reductions reverse ordering across pairs. Re-establish the optimizer on the distill objective. Complements `paper:muon-adamw-ft-gap`. Does not retarget Muon2.

## Key Contributions
1. Pretrain optimizer ranking is not the KL-distill ranking.
2. AdamW is the lowest-val-KL default in the measured short-horizon FKL setting.
3. Feasible Shampoo recipe choice can reverse conclusions.

## Empirical Highlights
AdamW lowest validation KL across the measured Qwen pairs. SOAP KL similar, slower. Shampoo reductions reverse across pairs.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.19419`
- Code: none found.
