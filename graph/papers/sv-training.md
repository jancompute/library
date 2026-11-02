---
id: paper:sv-training
type: paper
title: 'Steering Vectors as a Training Signal in LLM Post-Training'
authors:
- Tiejin Chen
- Maunil Vyas
- Huaiyuan Yao
- Hua Wei
year: 2026
month: 10
arxiv_id: '2610.40998'
url: https://arxiv.org/abs/2610.40998
methods:
- method:sv-training
cites:
- paper:olmo-3
- paper:minimax-m1
- paper:opd
tags:
- sft
- distillation
- rlvr
- active
---

# Steering Vectors as a Training Signal in LLM Post-Training

## Abstract Summary
Steering vectors can guide parameter updates, not only inference. A hidden-state hook during teacher-forced SFT/distill improves over plain SFT, with gains scaling with the off-policy gap and reaching 12% when distilling from thinking-mode teachers (three seeds). In GRPO, a correctness-contrast direction repairs advantages on wrong rollouts, including otherwise zero-gradient all-wrong groups. NeurIPS 2026.

## Key Contributions
1. Residual-stream steering as a train-time hook for SFT/distill and as GRPO advantage-repair on all-wrong groups.

## Empirical Highlights
Code github.com/tiejin98/sv_training. Failure boundaries: code generation can break the direction, cross-family layer transfer can break placement, inference-time application on an SV-trained checkpoint can break the regime. Does not retarget method:olmo-3, method:opd, or method:cispo.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.40998`
- Code: `https://github.com/tiejin98/sv_training` (`code_status: released`).
