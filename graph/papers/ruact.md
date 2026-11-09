---
id: paper:ruact
type: paper
title: 'RuACT: Rubrics as Adaptive Critics and Teachers'
authors:
- Yijun Li
- Zhengxi Lu
- Zhipiao Liu
- Jinzheng Yu
- Xutao Weng
- Jian Shao
- Yongliang Shen
year: 2026
month: 11
arxiv_id: '2611.09597'
url: https://arxiv.org/abs/2611.09597
methods:
- method:ruact
cites:
- paper:draco
- paper:vista
- paper:rcrl
tags:
- post-training
- rubric
- agentic
- active
---

# RuACT: Rubrics as Adaptive Critics and Teachers

## Abstract Summary
Under group-relative rubric RL, a criterion that every rollout fails (unreachable) or passes (saturated) contributes no within-group contrast. In Qwen3-4B medical GRPO, $60.88\%$ of query–rubric observations are inactive ($25.19\%$ unreachable / $35.69\%$ saturated). RuACT routes unreachable rubrics through privileged OPSD (Teacher) and saturated rubrics through child-rubric decomposition (Critic). ResearchQA $64.82\to 69.44$ vs GRPO. Code: `ZJU-REAL/RuACT`.

## Key Contributions
1. Diagnosis that inactive rubrics are two different missing-supervision states, not one reweighting problem.
2. Rubric as Teacher: privilege the unreachable criterion in OPSD, gated by a later unprivileged reward.
3. Rubric as Critic: split a saturated criterion into child rubrics that restore within-group contrast.

## Empirical Highlights
Qwen3-4B four-bench avg $56.52\to 59.12$; HealthBench $37.62\to 40.12$; 1.7B avg $45.04\to 47.17$. Does not retarget CANOPY or DRACO.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.09597`
- Code: `https://github.com/ZJU-REAL/RuACT` (`code_status: released`). Host: verl.
