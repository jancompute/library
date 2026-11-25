---
id: paper:recap
type: paper
title: 'RECAP: Training Long-horizon LLM Agents with Context Compaction'
authors:
- Yulun Jiang
- Maria Brbic
- Michael Moor
year: 2026
month: 11
arxiv_id: '2611.31258'
url: https://arxiv.org/abs/2611.31258
methods:
- method:recap
cites: []
tags:
- agents
- compaction
- grpo
---

# RECAP: Training Long-horizon LLM Agents with Context Compaction

## Abstract Summary
Task-reward GRPO with compaction leaves post-compaction action drift. RECAP trains summaries so compact history induces the same subsequent actions as the original history. Behavior-distortion KL splits into a summary reward and a post-compaction self-distillation term.

## Key Contributions
1. Behavior-distortion objective between compact-conditioned and full-context action distributions.
2. Complementary \(g_{\mathrm{sum}}\) plus \(g_{\mathrm{post}}\) on a GRPO host.
3. 32K working-window Qwen3.5-4B vs 128K GRPO without compaction.

## Empirical Highlights
Qwen3.5-4B 32K BrowseComp-Plus 62.8 vs GRPO 58.2 (+4.6); SWE-bench Verified 51.1 vs GRPO 46.8 (+4.3). 128K GRPO 63.8 / 55.5. \(\lambda=0.1\) BrowseComp / 0.03 SWE.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.31258`
- Code: `https://github.com/eth-medical-ai-lab/recap`
