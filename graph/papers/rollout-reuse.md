---
id: paper:rollout-reuse
type: paper
title: "Don't Discard Your Rollouts: Reusing Teacher RL Traces for Student Distillation"
authors:
- Vashisth Tiwari
- Emma Strubell
- J. Zico Kolter
year: 2026
month: 11
arxiv_id: '2611.26803'
url: https://arxiv.org/abs/2611.26803
methods:
- method:rollout-reuse
cites: []
tags:
- distillation
- opd
- grpo
- sft
- dpo
---

# Don't Discard Your Rollouts: Reusing Teacher RL Traces for Student Distillation

## Abstract Summary
Canonical distillation discards GRPO traces and regenerates from the final teacher. This paper reuses saved pass rates and teacher logp: pass-rate ordered SFT then mixed-success DPO with teacher-top1 selection. Across maths and coding, the two-stage recipe matches canonical distillation on average without extra teacher generation. Naive SFT on the same traces is 1.95 maths / 4.44 coding points below canonical. Gemma-2-2B MATH500 4.3%→17.1% with the SFT warm start.

## Key Contributions
1. Two-stage reuse of saved teacher GRPO traces (pass-rate SFT then mixed-success DPO).
2. Cached teacher-top1 selection instead of student scoring (GRAPE).
3. Multi-family student bake-off at zero extra teacher inference.

## Empirical Highlights
Maths avg@8 vs canonical −0.37 (95% CI includes 0); naive SFT −1.95. Avoids 58.3M maths + 17.6M coding regen tokens. NeurIPS 2026.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.26803`
- Code: `https://github.com/vashistht/rollout_reuse`
