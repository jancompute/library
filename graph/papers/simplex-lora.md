---
id: paper:simplex-lora
type: paper
title: 'SimplexLoRA: Dynamic Rank Updating via Alternating Minimization with Simplex Projection'
authors:
- 'Igor Shalygin'
- 'Grigorii Davydenko'
- 'Andrey Veprikov'
- 'Aleksey Antonov'
- 'Nikolay Bushkov'
- 'Stanislav Moiseev'
- 'Aleksandr Beznosikov'
year: 2026
month: 10
arxiv_id: '2610.37206'
url: https://arxiv.org/abs/2610.37206
methods:
- method:simplex-lora
cites:
- paper:lr-matters-lora
tags:
- peft
- lora
- active
---

# SimplexLoRA: Dynamic Rank Updating via Alternating Minimization with Simplex Projection

## Abstract Summary
Fixed-rank LoRA spends the same budget on every adapter. SimplexLoRA fits importance weights on an n-scaled simplex, freezes them, and reallocates rank without extra inference cost. EMNLP 2026 Findings.

## Key Contributions
1. SimplexLoRA as an active rank-allocation plug-in on task:lora-quality-tuning.

## Empirical Highlights
Matches or beats LoRA and adaptive-rank baselines on 12 tasks; largest gains at low ranks. Does not retarget method:lr-matters-lora.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.37206`
- Code: `https://github.com/brain-lab-research/SimplexLoRA (`code_status: released`).`
