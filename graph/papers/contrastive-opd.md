---
id: paper:contrastive-opd
type: paper
title: Contrastive On-Policy Distillation via Dual-Branch Supervision
authors:
- Zhibo Hou
- Fan Zhao
- Yiping Li
- Zhiyu An
- Wan Du
year: 2026
month: 11
arxiv_id: '2611.28359'
url: https://arxiv.org/abs/2611.28359
methods:
- method:contrastive-opd
cites: []
tags:
- distillation
- opd
- contrastive
- multi-teacher
---

# Contrastive On-Policy Distillation via Dual-Branch Supervision

## Abstract Summary
cOPD contrasts a strong teacher, a weak teacher, and the student at student prefixes. Dual-branch token masks keep tokens with a margin over both teachers. MUST NOT reuse slug `copd` (`method:copd` is black-box communicative OPD). Code promised on acceptance, none found.

## Key Contributions
1. Weak teacher as a contrastive reference, not only a worse imitation target.
2. Dual-branch Top-16 mask with \(\tanh(\Delta_v/\tau)\) log-odds contrast.
3. Math Pass@16, instruction following, and abstention QA across two student families.

## Empirical Highlights
JustRL config pooled Pass@16 77.46 vs JSD 75.14 / strong teacher 75.72. Qwen3 4B/0.6B/1.7B 65.32 vs W2S-OPD 57.80 (+7.52). Qwen3 IF 24.26 vs RKL +0.80; Llama IF 21.73 vs W2S-OPD +1.96.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.28359`
- Code: none found as of 2026-11-24
