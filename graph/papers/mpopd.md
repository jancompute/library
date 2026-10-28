---
id: paper:mpopd
type: paper
title: 'Proposing Better Rollouts for On-Policy Distillation'
authors:
- 'Sirui Chen'
- 'Yunzhe Qi'
- 'Haobo Xu'
- 'Jiaru Zou'
- 'Mengting Ai'
- 'Zihao Li'
- 'Jingrui He'
year: 2026
month: 10
arxiv_id: '2610.36477'
url: https://arxiv.org/abs/2610.36477
methods:
- method:mpopd
cites:
- paper:opd
tags:
- distillation
- opd
- active
---

# Proposing Better Rollouts for On-Policy Distillation

## Abstract Summary
Vanilla OPD samples from the current student, so the teacher must supervise traces it cannot reach and noise compounds. MPOPD builds a student-anchored, teacher-guided geometric-mixture proposal and samples it in one forward pass.

## Key Contributions
1. MPOPD as an active OPD rollout-proposal plug-in on task:student-distillation.

## Empirical Highlights
Qwen3-4B-Base math +6.91 vs OPD with 41% shorter outputs; gains on 16 math/knowledge/medical benches. Does not retarget method:opd.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.36477`
- Code: `https://github.com/csr16/MPOPD (`code_status: released`).`
