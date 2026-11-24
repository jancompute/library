---
id: paper:recurrent-student-opd
type: paper
title: Bridging Teacher–Student Capability Gaps with Recurrent Computation
authors:
- Zeyi Huang
- Jiuxiang Gu
- Eli Shechtman
- Yong Jae Lee
- Zongze Wu
year: 2026
month: 11
arxiv_id: '2611.28603'
url: https://arxiv.org/abs/2611.28603
methods:
- method:recurrent-student-opd
cites: []
tags:
- distillation
- opd
- recurrence
- architecture
---

# Bridging Teacher–Student Capability Gaps with Recurrent Computation

## Abstract Summary
Convert the student into cross-token recurrence (or Loop 3) in the same OPD fine-tune so a small backbone can absorb larger teachers. Recurrence avoids the vanilla teacher-size reversal seen in TF-KD pretrain. Distinct from ELR mixed-depth looping and Concertina teacher-layer folding. No public code.

## Key Contributions
1. Cross-token recurrence as student capacity at ~+3% params and \(1.1\times\) decode latency.
2. Joint architecture conversion + OPD from pretrained Qwen2.5-0.5B without repeating pretrain.
3. Recurrent students keep improving as teacher size grows; vanilla OPD plateaus.

## Empirical Highlights
From-scratch 0.4B + 3.9B teacher OPD: recurrent vs vanilla GSM8K +10.7 / MATH500 +6.0. Qwen2.5-0.5B + 7B teacher 57.5/41.6 vs vanilla OPD 53.7/37.6. Loop 3 sits between vanilla and recurrence.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.28603`
- Code: none found as of 2026-11-24
