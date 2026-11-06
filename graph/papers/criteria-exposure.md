---
id: paper:criteria-exposure
type: paper
title: 'Learning the Task or Learning the Verifier? Rethinking Criteria Exposure in Embodied Self-Improvement'
authors:
- Wenbo Huang
- Jianxin Bi
- Shunyu Yang
- Ruiyang Si
- Rui Ni
- Qiang Wang
- Shulong Jiang
- Yintianrun Zhang
- Feixiang Ruan
- Kewei Zhang
- Ye Huang
- Shukai Gong
- Daquan Zhou
year: 2026
month: 11
arxiv_id: '2611.08318'
url: https://arxiv.org/abs/2611.08318
methods:
- method:neohorse-1
cites:
- paper:neohorse-1
- paper:rsi-dojo
tags:
- rsi
- eval
- gotcha
---

# Learning the Task or Learning the Verifier? Rethinking Criteria Exposure in Embodied Self-Improvement

## Abstract Summary
Criteria Exposure (CE) lets a self-improving embodied coding agent read the benchmark's success criteria. With CE, libraries score $51.6\%$ vs $27.8\%$ under the original criteria on 16 criteria-limited RoboDojo tasks, but the lead vanishes under instruction-faithful criteria ($45.0\%$ vs $47.2\%$). Skills transfer poorly across tasks and to LIBERO-PRO / RoboCasa365. Instruction-faithful criteria better match the language instruction.

## Key Contributions
1. Treats verifier exposure as an experimental factor, not an implementation detail.
2. CE gains follow the criteria the learner read; they do not survive a criteria rewrite that still matches the instruction.
3. Practical rule: learner sees only success a robot would see; criteria verify what the instruction says.

## Empirical Highlights
Gotcha on `task:agentic-rsi-routing-posttrain`. Project page `https://dagroup-pku.github.io/PyRUA-Lean/RSIJudge`. Does not retarget NeoHorse-1.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.08318`
- Project: `https://dagroup-pku.github.io/PyRUA-Lean/RSIJudge`
- Code: none found (`code_status: none`).
