---
id: paper:reframe
type: paper
title: 'Reframe: Observation-Aligned Multi-Teacher On-Policy Distillation for Agentic Visual Reasoning'
authors:
- Haozhi Yuan
- Handong Li
- Yifan Zhang
- Qianshan Wei
year: 2026
month: 11
arxiv_id: '2611.12886'
url: https://arxiv.org/abs/2611.12886
methods:
- method:reframe
cites:
- paper:open-mopd
- paper:opd
tags:
- distillation
- mopd
- vision
- grpo
- active
---

# Reframe

## Abstract Summary
Reframe pairs GD-GRPO with OG-MOPD so multimodal teachers are aligned at the observation, not just the prompt. Qwen3.5-9B image avg $63.46\to 69.48$ ($+6.02$), video $49.75\to 53.10$ ($+3.35$) vs Mix-RL $66.75/51.41$ and MOPD $68.19/52.32$. Code EliYuan30/Reframe released. HF Daily leftover (cs.CV) ingested 2026-11-10. Paper MOPD is not the library $83.4\%$ bake-off. Does not replace Open-MOPD.

## Key Contributions
1. Observation-aligned teacher mix for VL agents (OG-MOPD).
2. GD-GRPO host that keeps group-relative updates while teachers share the same observation.
3. Released trainer.

## Empirical Highlights
Image $+6.02$ / video $+3.35$ vs Mix-RL and MOPD on Qwen3.5-9B. Does not retarget Open-MOPD.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.12886`
- Code: `https://github.com/EliYuan30/Reframe` (`code_status: released`).
