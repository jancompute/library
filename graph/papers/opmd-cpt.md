---
id: paper:opmd-cpt
type: paper
title: 'Beyond Passive Imitation: On-Policy Mid-Training Distillation for Language Models'
authors:
- Ruize Zheng
- Xuyang Liu
- Siyu Ren
- Xiaobing Tu
- Yinggui Wang
- Jinkui Ren
- Xiantao Zhang
- Linfeng Zhang
year: 2026
month: 11
arxiv_id: '2611.13855'
url: https://arxiv.org/abs/2611.13855
methods:
- method:opmd-cpt
cites:
- paper:opd
- paper:opmd
tags:
- distillation
- continued-pretrain
- mid-training
- opd
- active
---

# Beyond Passive Imitation: On-Policy Mid-Training Distillation for Language Models

## Abstract Summary
NTP mid-training on 1B MegaMath-Web-Pro tokens improves Llama-3.2-3B and collapses Qwen3-1.7B-Base (MATH-500 pass@16 $76.6\to 18.2$). OPMD-CPT rollouts from high-entropy corpus anchors with frozen-teacher reverse-KL and raises MATH-500 to $82.8$ / Minerva $30.5\to 34.9$–$36.0$. Distinct from post-train OPMD (`arXiv:2610.14022`). GitHub ShuidiH20/OPMD 404 as of 2026-11-11.

## Key Contributions
1. Model-dependent NTP CPT failure: same corpus, Llama improves, Qwen collapses.
2. Anchor Token Identification then on-policy reverse-KL mid-training.
3. 4B and 14B teachers yield comparable MATH-500 pass@16.

## Empirical Highlights
Qwen3-1.7B-Base MATH-500 pass@16 $76.6\to 82.8$ vs NTP $18.2$; avg@16 $18.5\to 30.5$. Minerva pass@16 $30.5\to 34.9$ (4B teacher) / $36.0$ (14B). Does not retarget OPD or `method:opmd`.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.13855`
- Code: `https://github.com/ShuidiH20/OPMD` (`code_status: announced`; 404 as of 2026-11-11).
