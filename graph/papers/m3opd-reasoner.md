---
id: paper:m3opd-reasoner
type: paper
title: 'M3OPD-Reasoner: An Open Recipe for Post-Training Multimodal Reasoning with Multi-Teacher On-Policy Distillation'
authors:
- Nguyen Quang Trung
- Hoang Phan
- Shuo Sun
- Longyin Zhang
- AiTi Aw
year: 2026
month: 11
arxiv_id: '2611.23034'
url: https://arxiv.org/abs/2611.23034
methods:
- method:m3opd-reasoner
cites: []
tags:
- distillation
- mopd
- vision
- gspo
- active
---

# M3OPD-Reasoner: An Open Recipe for Post-Training Multimodal Reasoning with Multi-Teacher On-Policy Distillation

## Abstract Summary
Open VLM recipe: per-domain GSPO teachers (image STEM, image perception, video), then MOPD (top-32 reverse-KL) into one student, then MixRL on the same 193K prompts. Qwen3.5-9B 21-bench avg@8: MixRL 74.4 vs MOPD+MixRL 75.9 (STEM 77.1 / perception 81.9 / video 64.1); GSPO teachers dagger overall 75.2. Paper MOPD is not the library 83.4% bake-off. Code ngquangtrung57/M3OPD-Reasoner. Does not retarget Open-MOPD or Reframe.

## Key Contributions
1. Domain GSPO teachers from Qwen3.5-9B without an SFT warm-up beat SFT-then-GSPO teachers.
2. MOPD of those teachers matches teacher domain means, then MixRL still improves the student with no collapse.
3. Releases M3OPD-SFT-1.35M, M3OPD-RL-193K, training code, and every-stage checkpoints.

## Empirical Highlights
Qwen3.5-9B 21 benches avg@8: MixRL 74.4; GSPO teachers 75.2; MOPD 75.2; M3OPD-Reasoner-9B (MOPD+MixRL) 75.9 / STEM 77.1 / perception 81.9 / video 64.1.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.23034`
- Code: `https://github.com/ngquangtrung57/M3OPD-Reasoner` (`code_status: released`; size 1069 as of 2026-11-18).
