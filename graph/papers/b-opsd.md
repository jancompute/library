---
id: paper:b-opsd
type: paper
title: 'B-OPSD: On-Policy Self-Distillation with Self-Generated Problem Briefs'
authors:
- Zhi Xu
- Yinqi Wu
- Feng Zhang
- Xiaotong Zhang
- Hong Yu
- Han Liu
year: 2026
month: 11
arxiv_id: '2611.19273'
url: https://arxiv.org/abs/2611.19273
methods:
- method:b-opsd
cites: []
tags:
- opsd
- privileged-teacher
- label-free
- active
---

# B-OPSD: On-Policy Self-Distillation with Self-Generated Problem Briefs

## Abstract Summary
OPSD usually conditions the teacher on a gold solution. B-OPSD generates a problem brief from the question alone (principles, applicability, pitfalls; no answer) and uses it as privileged teacher context. No GT during training. Both variants beat OPSD average accuracy at each of three Qwen3 sizes on AIME24 / AIME25 / HMMT25. Distinct from `method:bopd`. Code ZevineXu/B-OPSD. Does not retarget VISTA / u-OPSD.

## Key Contributions
1. Replaces gold solutions with self-generated problem briefs.
2. Frozen teacher matches the student on-policy under that brief.
3. Two brief-source variants (init vs saved student checkpoint).

## Empirical Highlights
Higher average accuracy than OPSD at each of three Qwen3 sizes on AIME24 / AIME25 / HMMT25.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.19273`
- Code: `https://github.com/ZevineXu/B-OPSD` (`code_status: released`).
