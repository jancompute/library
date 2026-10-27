---
id: paper:steer-teacher
type: paper
title: 'Steering the Teacher: Improving On-Policy Self-Distillation for Thinking Models'
authors:
- 'Tiejin Chen'
- 'Xiaoou Liu'
- 'Hanyang Chen'
- 'Hua Wei'
year: 2026
month: 10
arxiv_id: '2610.34005'
url: https://arxiv.org/abs/2610.34005
methods:
- method:steer-teacher
cites:
- paper:vista
tags:
- distillation
- opsd
- active
---

# Steering the Teacher: Improving On-Policy Self-Distillation for Thinking Models

## Abstract Summary
Privileged OPSD teachers that see the reference start citing it and suppress reconsideration. ST-OPSD steers two activation directions on the teacher only while the student learns the steered distributions.

## Key Contributions
1. Steered-Teacher OPSD as an active plug-in on task:privileged-teacher-opsd.

## Empirical Highlights
AIME/HMMT: accuracy over vanilla OPSD; reconsideration and reference-hallucination rates return to base-model levels. Does not retarget method:vista.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.34005`
- Code: `none found (`code_status: none`).`
