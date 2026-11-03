---
id: paper:bernoulli-opd
type: paper
title: 'Bernoulli On-Policy Distillation: Don''t Ignore High-Confidence Student Tokens'
authors:
- 'Mingyu Cao'
- 'Yaokai Jin'
- 'Shiwei Liu'
- 'Lu Yin'
year: 2026
month: 11
arxiv_id: '2611.02093'
url: https://arxiv.org/abs/2611.02093
methods:
- method:bernoulli-opd
cites:
- paper:opd
tags:
- opd
- token-matching
- active
---

# Bernoulli On-Policy Distillation: Don't Ignore High-Confidence Student Tokens

## Abstract Summary
Sampled reverse-KL OPD suppresses updates on high-confidence student tokens even when the teacher still disagrees. Bernoulli OPD matches teacher and student probabilities for the sampled token, a bounded probability-space correction that keeps disagreement without confidence-dependent suppression.

## Key Contributions
1. Bernoulli token-probability matching that restores OPD signal on high-confidence student tokens.

## Empirical Highlights
Fixed-rollout analyses restore optimization signal to high-confidence tokens while remaining sensitive to teacher-student disagreement. Code github.com/duterscmy/Bernoulli-OPD.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.02093`
- Code: `https://github.com/duterscmy/Bernoulli-OPD` (`code_status: released`).
