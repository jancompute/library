---
id: paper:eca
type: paper
title: 'Evidence-based Credit Assignment: Grounding Step-Level Rewards in Retrieved Documents'
authors:
- Wen Wang
- Jindong Wang
- Jiahua Bao
- Tu Yongsiqi
- Yihao Liu
- Junwei He
- Wenkui Fan
year: 2026
month: 11
arxiv_id: '2611.23824'
url: https://arxiv.org/abs/2611.23824
methods:
- method:eca
cites: []
tags:
- credit-assignment
- search-agent
- evidence
- grpo
- active
---

# Evidence-based Credit Assignment

## Abstract Summary
ECA assigns step-level credit from retrieved-document evidence rather than from the final answer. Φ(D) is an evidence-only potential; ECA-Horizon / ECA-TD / ECA-MC are variants. Vs GRPO: Qwen2.5-3B/7B macro EM +1.03 / +4.80 (3B 45.80 vs 44.77; 7B 51.60 vs 46.80). Distinct from GCA, EG-GRPO, Iris. No public train code (`code_status: none`; Snowball0823/ECA is unrelated). Does not retarget Iris.

## Key Contributions
1. Evidence-only potential Φ(D) from retrieved documents.
2. Horizon, TD, and MC instantiations on a GRPO host.
3. Deep-search QA gains over GRPO, GCA-style, and EG-GRPO-style credit.

## Empirical Highlights
Qwen2.5-3B 45.80 vs GRPO 44.77; 7B 51.60 vs 46.80 macro EM.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.23824`
- Code: `none found` (`code_status: none`; Snowball0823/ECA is unrelated).
