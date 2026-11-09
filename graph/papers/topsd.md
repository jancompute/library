---
id: paper:topsd
type: paper
title: 'TOPSD: Teachable On-Policy Self-Distillation'
authors:
- Jaewon Cho
- Minseo Yoon
- Jinyoung Park
- Jinwoo Seo
- Jaewon Chu
- Alice Oh
- Hyunwoo J. Kim
year: 2026
month: 11
arxiv_id: '2611.08179'
url: https://arxiv.org/abs/2611.08179
methods:
- method:topsd
cites:
- paper:vista
tags:
- distillation
- opsd
- multilingual
- active
---

# TOPSD: Teachable On-Policy Self-Distillation

## Abstract Summary
Privileged teachers drift: as errors accumulate in a student prefix, the teacher starts following the student's mistakes (Teacher Drift). TOPSD keeps only teachable prefixes and verifies that the teacher can recover from those prefixes before applying OPSD. Qwen3-1.7B/4B/8B PolyMath High Avg@3 $11.60$ / $17.79$ / $25.12$ ($+1.65$ / $+1.07$ / $+2.64$ vs strongest baseline). No public code as of 2026-11-09.

## Key Contributions
1. Teacher Drift as a privileged-OPSD failure mode.
2. Teachable Prefix Selection plus Teacher Recoverability Verification.
3. Gains concentrated on low- and medium-resource PolyMath languages.

## Empirical Highlights
Table 1 PolyMath High ten-language Avg@3. Pass@3 $18.72$ / $26.00$ / $35.28$. Does not retarget VISTA.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.08179`
- Code: none found (`code_status: none`).
