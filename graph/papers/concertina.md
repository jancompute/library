---
id: paper:concertina
type: paper
title: 'Folding Language Models into Themselves'
authors:
- Ziyang Zhang
- Yubin Jing
- Yuyao Li
- Haofan Wang
- Yichen Gong
year: 2026
month: 11
arxiv_id: '2611.18113'
url: https://arxiv.org/abs/2611.18113
methods:
- method:concertina
cites: []
tags:
- distillation
- looped-lm
- folding
- active
---

# Folding Language Models into Themselves

## Abstract Summary
Concertina folds every N adjacent teacher layers into a shared looped block, initializes low-rank step corrections from the replaced layers, and distills with FKL+CE. Qwen3-4B N=2 → 2.27B (57%) on 22B tokens retains 84% of the teacher on an 8-task avg. Not reverse-KL OPD. Code myboker/concertina. Does not retarget OPD.

## Key Contributions
1. Student built from teacher weights by folding adjacent layers, not trained from scratch.
2. SVD-init low-rank corrections plus a per-token gate at each loop step.
3. 35/55/10 math/knowledge/web mix; FKL+CE rather than reverse-KL matching.

## Empirical Highlights
Base-7 92%, GSM8K 90%, MATH 88%, 84% avg of teacher. Beats Qwen3-1.7B (36T) on 6/8. Same-size dense student +8–11 MMLU family / ~41× GSM8K.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.18113`
- Code: `https://github.com/myboker/concertina` (`code_status: released`).
