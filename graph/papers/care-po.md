---
id: paper:care-po
type: paper
title: 'CARE-PO: Controllable Tool-Call Efficiency for LLM Agents'
authors:
- Xiaoyang Ye
- Xiao Yao
- Hairui Zhu
- Yiying Yang
- Bei Gan
- Jinliang Lu
- Tengjin Weng
- Yuan Yao
- Wenhao Jiang
year: 2026
month: 11
arxiv_id: '2611.12125'
url: https://arxiv.org/abs/2611.12125
methods:
- method:care-po
cites: []
tags:
- agentic
- efficiency
- tool-use
- active
---

# CARE-PO

## Abstract Summary
CARE-PO is a GRPO-family agent trainer with a fixed per-task reference budget. Advantages are relative to that budget rather than a learned efficiency reward. 5 of 6 GAIA operating points improve success and call count; the sixth matches success at $58.6\%$ fewer calls. A 27B efficiency-reward baseline collapses to zero calls; CARE-PO does not. No public code as of 2026-11-10. Does not replace CANOPY or Iris.

## Key Contributions
1. Anchor tool-call count to a fixed per-task reference instead of a learned efficiency head.
2. Relative efficiency advantage that cannot reward zero-call collapse.
3. GAIA operating-point grid plus a 27B collapse ablation.

## Empirical Highlights
5/6 GAIA points improve success and calls; sixth matches success at $58.6\%$ fewer calls. Efficiency-reward 27B $\to$ zero calls. Does not retarget CANOPY.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.12125`
- Code: none found (`code_status: none`).
