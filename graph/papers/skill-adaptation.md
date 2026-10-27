---
id: paper:skill-adaptation
type: paper
title: 'Evolving to Match Capabilities: Improving Harness Self-Evolution via Skill Adaptation'
authors:
- 'Zhihao Yang'
- 'Haojin Wang'
- 'Juncheng Wu'
- 'Kuan Zhang'
- 'Yukun Chen'
- 'Run Luo'
- 'Yaojie Lu'
- 'Yuyin Zhou'
- 'Lu Wang'
- 'Xianpei Han'
year: 2026
month: 10
arxiv_id: '2610.33024'
url: https://arxiv.org/abs/2610.33024
methods:
- method:skill-adaptation
cites:
- paper:harness-playbook
- paper:rrsi
tags:
- agent-harness
- active
---

# Evolving to Match Capabilities: Improving Harness Self-Evolution via Skill Adaptation

## Abstract Summary
Harness skills that help a strong model can hurt a weak one (GPT-5.6-luna +31.1 vs Gemma-4-E4B -8.8 on 103 pairs). In 86% of failed weak runs the violated requirement is already in the skill. Skill adaptation rewrites skills to the executor. HF Daily 2026-10-27. Project https://zhihaoyang30.github.io/skill-adaptation/

## Key Contributions
1. Skill adaptation as an active plug-in on task:agent-harness-runtime.

## Empirical Highlights
Diagnoses tool/context failures and reformulates skills. Does not retarget method:omp2-harness.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.33024`
- Code: `https://zhihaoyang30.github.io/skill-adaptation/ (`code_status: announced`).`
