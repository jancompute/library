---
id: paper:opd-backdoor-propagation
type: paper
title: 'On-policy distillation as a Backdoor Propagation Channel'
authors:
- Zane Fu
- Yanzhao Zheng
- Ziting Qin
- Qianshan Wei
- Yi Yu
- Gongli Xi
- Jihuai Zhu
- Baohua Dong
- Hangcheng Zhu
- Ruohui Huang
- Gang Yu
year: 2026
month: 11
arxiv_id: '2611.19207'
url: https://arxiv.org/abs/2611.19207
methods:
- method:opd
cites: []
tags:
- opd
- safety
- backdoor
- gotcha
- active
---

# On-policy distillation as a Backdoor Propagation Channel

## Abstract Summary
Claim note, no trainer. An SFT-implanted conditional backdoor in the teacher transfers to the student under OPD with extremely small trigger-prompt exposure, and more strongly than under conventional distillation. The channel is anomalous triggered-versus-clean teacher conditional probabilities, internalized into student representations. Complements `paper:opd-safety-backdoor` (poisoned safety-teacher OPD). Distinct mechanism: teacher SFT backdoor then OPD transfer. Does not retarget OPD matching.

## Key Contributions
1. Teacher SFT backdoor plus OPD is an efficient cross-model propagation channel.
2. Tiny trigger exposure suffices; stronger than conventional distill.
3. Source-side suppression of anomalous teacher conditionals as a mitigation direction.

## Empirical Highlights
OPD transfers a teacher SFT backdoor with extremely small trigger exposure, stronger than conventional distillation.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.19207`
- Code: none found.
