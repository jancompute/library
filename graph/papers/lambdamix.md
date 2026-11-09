---
id: paper:lambdamix
type: paper
title: 'LambdaMix: Learning Preference-Conditioned Adapter Mixtures with Group-Relative Online RL'
authors:
- Constantinos Karouzos
- Nikolaos Aletras
year: 2026
month: 11
arxiv_id: '2611.09634'
url: https://arxiv.org/abs/2611.09634
methods:
- method:lambdamix
cites:
- paper:corrgrpo
- paper:dara
tags:
- post-training
- peft
- multi-reward
- active
---

# LambdaMix: Learning Preference-Conditioned Adapter Mixtures with Group-Relative Online RL

## Abstract Summary
LambdaMix jointly trains one LoRA per objective on a frozen base and uses a preference vector both to mix adapters at generation time and to weight separately normalized rewards in a group-relative online update. One run produces a family of policies that can be reweighted at inference. Qwen3.5-9B PKU-SafeRLHF HV $0.8735$ vs prompt conditioning $0.7760$; GSM8K-IF HV $0.8099$ vs GRPO $0.6947$. Code: `ckarouzos/lambdamix`.

## Key Contributions
1. Per-objective LoRA adapters mixed by a preference vector at generate and update time.
2. Separately normalized rewards (GDPO-style) before preference weighting.
3. One training run (32k completions) vs a GRPO specialist bank (5 runs / 160k) for the same preference sweep.

## Empirical Highlights
Table 1 Qwen3.5-9B: PKU-SafeRLHF HV $0.8735$ with spans $1.931$ / $1.982$; GSM8K-IF HV $0.810$. Does not retarget CorrGRPO / DARA aggregation.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.09634`
- Code: `https://github.com/ckarouzos/lambdamix` (`code_status: released`).
