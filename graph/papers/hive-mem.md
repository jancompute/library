---
id: paper:hive-mem
type: paper
title: 'HiVe-Mem: Interleaving Horizontal Memory Expansion and Vertical Evidence Composition for Multimodal Agents'
authors:
- Haozhen Zhang
- Bohan Liu
- Jianzhu Bao
- Qingyuan Liu
- Haodong Yue
- Xiao Li
- Zi Pong Lim
- Wenya Wang
year: 2026
month: 11
arxiv_id: '2611.12872'
url: https://arxiv.org/abs/2611.12872
methods:
- method:hive-mem
cites: []
tags:
- agent-memory
- multimodal
- retrieval
- active
---

# HiVe-Mem: Interleaving Horizontal Memory Expansion and Vertical Evidence Composition for Multimodal Agents

## Abstract Summary
Tuesday leftover (listing high of 2026-11-10, not ingested then). Multimodal agent memory: horizontal expansion, vertical evidence composition, and a trainable selector. ~90% token cut (0.658M vs 7.812M). Qwen3-VL-4B F1/LJ 32.32/57.96. Code `ViktorAxelsen/HiVe-Mem` (`code_status: released`). Distinct from `method:hive-synth`. Does not retarget ACE.

## Key Contributions
1. Horizontal expansion retrieves neighboring memories instead of a single compressed hit.
2. Vertical composition stacks heterogeneous evidence for the current query.
3. A trainable selector chooses which view to expose, rather than a fixed memory schema.

## Empirical Highlights
~90% token cut (0.658M vs 7.812M). Qwen3-VL-4B F1/LJ 32.32/57.96. Distinct from write-time playbooks (ACE) and from Hive-Synth pretrain data.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.12872`
- Code: `https://github.com/ViktorAxelsen/HiVe-Mem` (`code_status: released`).
