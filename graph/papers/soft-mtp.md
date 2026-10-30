---
id: paper:soft-mtp
type: paper
title: 'Multi-Token Prediction Done Right'
authors:
- 'Jayden Teoh'
year: 2026
month: 10
arxiv_id: '2610.38331'
url: https://arxiv.org/abs/2610.38331
methods:
- method:soft-mtp
cites:
- paper:echo-mtp
tags:
- mtp
- distillation
- active
---

# Multi-Token Prediction Done Right

## Abstract Summary
Standard MTP cross-entropy splits into a KL self-distillation term that pulls each MTP head toward the model's NTP distribution and a noisy residual that buries that signal at scale. Soft-MTP recovers the KL gradient by combining the two CE gradients through straight-through routing, with no vocabulary-sized logit matrices.

## Key Contributions
1. One-line MTP gradient fix that keeps the KL self-distillation term and drops the noisy residual.

## Empirical Highlights
Code github.com/JaydenTeoh/Soft-MTP. Compatible with fused CE kernels. Mention on task:pretrain-dense-7b. Does not retarget method:uno.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.38331`
- Code: `https://github.com/JaydenTeoh/Soft-MTP (`code_status: released`).`
