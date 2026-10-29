---
id: paper:memory-tax
type: paper
title: 'Memory Tax: Dissecting the Net Value of Agent Memory'
authors:
- 'Xuan He'
- 'Sining Zhoubian'
- 'Ruozhen Yang'
- 'Yuhao Wen'
- 'Zhineng Wang'
- 'Yuyang Hu'
- 'Ke Yang'
- 'Yuyu Zhang'
- 'Ping Nie'
- 'Jiawei Han'
- 'ChengXiang Zhai'
year: 2026
month: 10
arxiv_id: '2610.34073'
url: https://arxiv.org/abs/2610.34073
methods:
- method:ace
cites:
- paper:ace
- paper:luck-carrying-lessons
tags:
- agent-memory
- gotcha
---

# Memory Tax: Dissecting the Net Value of Agent Memory

## Abstract Summary
Net value of agent memory vs naive RAG over raw history. Eleven memory systems on LongMemEval-s / PersonaMem-v2 / MINT-Eval across Qwen3.5-4B, Qwen3.6-27B, and GPT-5.6 Luna; many underperform two-round RAG. Memory solves some queries RAG misses (benefit) and loses others RAG already solves (tax). Complements paper:luck-carrying-lessons.

## Key Contributions
1. Memory-tax gotcha on task:agent-memory; not an ACE replacement.

## Empirical Highlights
RAG (2rd) LongMemEval-s 72.2 / 81.4 / 90.0 on the three backbones; OpenViking −40.4 / −22.6 / −27.0 vs that RAG. Keep a raw-history retrieval path. Distinct from 2610.29823 (different short note, not ingested). Does not retarget ACE.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.34073`
- Code: `none found (`code_status: none`).`
