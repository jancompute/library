---
id: paper:muon-sw-tuning-gap
type: paper
title: 'Tune the Baseline First: Most of Muon''s Scaled Weight Decay Gain Is a Tuning Gap, but Its Small Real Advantage Grows With Model Size'
authors:
- 'Esther Xin'
year: 2026
month: 11
arxiv_id: '2611.02529'
url: https://arxiv.org/abs/2611.02529
methods:
- method:muon2
cites:
- paper:muon2
tags:
- muon
- gotcha
---

# Tune the Baseline First: Most of Muon's Scaled Weight Decay Gain Is a Tuning Gap, but Its Small Real Advantage Grows With Model Size

## Abstract Summary
Muon-SW comparisons usually reuse one LR/WD setting. Under MAI-Base-2 joint LR*WD tuning on a 1.9M-15M active MoE ladder, ~90% of the 0.035 BPB Muon-SW gain is a tuning gap (tuned gap 0.0026 BPB, 95% CI [0.0018, 0.0034], 1.03x). The leftover advantage is real (4/4 seeds at the smallest size) and grows with scale (0.0036 to 0.0051 BPB).

## Key Contributions
1. Most reported Muon-SW gain is a shared-HP tuning gap; a small real gap grows with model size.

## Empirical Highlights
Gotcha on method:muon2. Does not retarget Muon2. Code github.com/ethxin0011/weight_decay_ladder.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.02529`
- Code: `https://github.com/ethxin0011/weight_decay_ladder` (`code_status: released`).
