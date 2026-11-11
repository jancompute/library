---
id: paper:camp-ii
type: paper
title: 'Coding Agent Memory Post-Training II: Unlocking the Memory Potential of Pre-trained File Operations for Long-Horizon Tasks via On-Policy Distillation'
authors:
- Lirui Luo
- Kelong Mao
- Xinwei Yang
- Rongqing Li
- Luyu Chen
- Kieran Wong
- Yudong Guo
- Xinrui Wang
- Jiayin Zhu
- Gu Simiu
- Sulong Xu
- Cong Fang
year: 2026
month: 11
arxiv_id: '2611.14009'
url: https://arxiv.org/abs/2611.14009
methods:
- method:camp-ii
cites:
- paper:opd
tags:
- agent-memory
- opd
- files
- continual-learning
- active
---

# Coding Agent Memory Post-Training II

## Abstract Summary
Dedicated memory tools weaken OPD because the teacher has no prior for the interface. CAMP-II uses ordinary Bash files as memory and trains one Qwen3.5 policy across CAMG-II with asynchronous OPD. CAMG-II mean $64.6$ vs CAMP-I $54.2$ ($2.97\times$ the strongest OPD-baseline gain). Terminal-Bench 2.1 $23.1\to 30.0$ (4B) / $38.0$ (9B). No public code as of 2026-11-11.

## Key Contributions
1. Shared file-operation prior as the memory interface for OPD.
2. CAMG-II: Shop / Coding / AutoResearch / General / Visual with episode-persistent workspace.
3. Fully asynchronous OPD jointly across the five environments.

## Empirical Highlights
CAMG-II $64.6$ vs CAMP-I $54.2$. CAMP-II-9B TB 2.1 $38.0$ / SWE-Bench Pro V2 $30.1$ vs Qwen3.5-35B-A3B $33.8$ / $27.4$. Masking memory-write tokens removes the gain. Does not retarget ACE.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.14009`
- Code: none found (`code_status: none`).
