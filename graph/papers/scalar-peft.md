---
id: paper:scalar-peft
type: paper
title: 'Direction or Magnitude? Learning Scalars over Task-Calibrated Directions'
authors:
- Ziqing Wen
- Xiaohui Song
- Jiahuan Wang
- Ping Luo
- Junlin Zeng
- Dongsheng Li
- Kele Xu
- Tao Sun
year: 2026
month: 11
arxiv_id: '2611.17784'
url: https://arxiv.org/abs/2611.17784
methods:
- method:scalar-peft
cites: []
tags:
- peft
- lora
- scalars
- active
---

# Direction or Magnitude? Learning Scalars over Task-Calibrated Directions

## Abstract Summary
SCALAR freezes an activation-derived input basis and a random output dictionary, then trains only layer-specific scalars. Qwen2.5-7B commonsense 88.9 vs LoRA r=8 88.8 at ~1/25 params; LLaMA3-8B 87.3 vs 87.4 at ~1/23; peak mem −20%, throughput +6% on 2× H20. No public code. Does not retarget vanilla LoRA + rsLoRA + LR sweep.

## Key Contributions
1. PEFT quality attributed to a task-calibrated direction more than to a learned low-rank magnitude.
2. Layer-specific scalars are the only trainable parameters.
3. Matched LoRA r=8 commonsense with a large parameter and memory cut.

## Empirical Highlights
Qwen2.5-7B 88.9 vs LoRA 88.8 (~1/25 params). LLaMA3-8B 87.3 vs 87.4 (~1/23). Peak mem −20%; throughput +6%.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.17784`
- Code: none found (`code_status: none`).
