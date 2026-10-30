---
id: paper:scope-agent-opsd
type: paper
title: 'SCOPE: Selective Critical-Step On-Policy Self-Distillation for Agentic Reinforcement Learning'
authors:
- 'Qirui Liu'
- 'Wei Cao'
- 'Yu Mi'
- 'Yichen Sun'
- 'Xuekun Zhang'
- 'Lei Liu'
- 'Yue Shen'
- 'Zhixuan Chu'
year: 2026
month: 10
arxiv_id: '2610.38391'
url: https://arxiv.org/abs/2610.38391
methods:
- method:scope-agent-opsd
cites:
- paper:canopy
tags:
- opsd
- agent-rl
- active
---

# SCOPE: Selective Critical-Step On-Policy Self-Distillation for Agentic Reinforcement Learning

## Abstract Summary
After SFT warm-up the policy writes step-specific hindsight skills and distills them only at selected error steps. A bounded signed teacher-student coefficient keeps the auxiliary OPSD from reversing RL signs. A success-relative pairwise length reward shortens successful traces.

## Key Contributions
1. Critical-step OPSD on long-horizon agents, distinct from method:scope-opsd and method:scope-t2i.

## Empirical Highlights
Qwen2.5-3B ALFWorld 97.7 / WebShop 85.2 vs SEED +5.9/+6.3pp; unseen ALFWorld 89.6 vs GRPO +23.2pp with 46.7% fewer interactions. Qwen3-32B seen 99.2 / unseen 94.0. No public code. Does not retarget method:canopy.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.38391`
- Code: `none found (`code_status: none`). Distinct from method:scope-opsd and method:scope-t2i.`
