---
id: paper:swe-ladder
type: paper
title: 'SWE-Ladder: Learning to Localize, Reproduce, and Patch via Progressive Privileged Self-Distillation'
authors:
- 'Xudong Cai'
- 'Zhengxi Lu'
- 'Yuchen Yan'
- 'Jian Shao'
- 'Jun Xiao'
- 'Yueting Zhuang'
- 'Yongliang Shen'
year: 2026
month: 10
arxiv_id: '2610.33667'
url: https://arxiv.org/abs/2610.33667
methods:
- method:swe-ladder
cites:
- paper:vista
- paper:canopy
tags:
- distillation
- swe
- active
---

# SWE-Ladder: Learning to Localize, Reproduce, and Patch via Progressive Privileged Self-Distillation

## Abstract Summary
SWE repair has localize/reproduce/patch stages. GRPO only sees the final test; full-patch OPSD leaks the whole diff at every step. SWE-Ladder routes each tool step to stage-matched privileged evidence and distills in repair order.

## Key Contributions
1. SWE-Ladder as an active plug-in on task:privileged-teacher-opsd.

## Empirical Highlights
Qwen3-4B-Instruct R2E-Gym SWE-bench Verified pass@1 9.6 to 16.4 vs GRPO 10.4 / full-patch OPSD 12.4. OpenHands 13.0 to 17.6. Reversed stage order 11.4. Code sekongger/SWE-Ladder.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.33667`
- Code: `https://github.com/sekongger/SWE-Ladder (`code_status: released`).`
