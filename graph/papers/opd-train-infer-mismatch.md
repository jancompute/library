---
id: paper:opd-train-infer-mismatch
type: paper
title: 'How Much Training-Inference Mismatch Can On-Policy Distillation Tolerate?'
authors:
- Cong Yu
- Ziting Wang
- Songlin Jiang
- Sitong Zhang
- Chengliang Chai
- Youhe Jiang
- Eiko Yoneki
- Tuo Shi
year: 2026
month: 11
arxiv_id: '2611.11450'
url: https://arxiv.org/abs/2611.11450
methods:
- method:opd
cites:
- paper:opd
tags:
- distillation
- opd
- train-infer-mismatch
- fp8
- gotcha
---

# OPD Train–Inference Mismatch

## Abstract Summary
OPD still learns when sampler and trainer disagree in ways that collapse RL. First/last-layer BF16 with FP8 in between plus async rollout is $1.62\times$ vs sync BF16; KV $1.93\times$ vs BF16. All-layer FP8 fails. Code benyucong/train-inference-mismatch-opd released. Complements CIS-RL / TRACE / TRIAGE (those are RL mismatch). Does not retarget OPD.

## Key Contributions
1. Reverse-KL OPD is more mismatch-tolerant than on-policy RL.
2. Keep first and last layers in BF16; do not quantize every layer.
3. Released mismatch trainer.

## Empirical Highlights
FP8 first/last BF16 + async $1.62\times$ vs sync BF16; $1.93\times$ KV. All-layer FP8 is the failure. Does not retarget OPD.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.11450`
- Code: `https://github.com/benyucong/train-inference-mismatch-opd` (`code_status: released`).
