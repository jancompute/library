---
id: paper:rlvr-sharpens
type: paper
title: 'RLVR Sharpens the Pencil, Not the Mind'
authors:
- 'Shreeyam Bangera'
- 'Manya Gupta'
year: 2026
month: 11
arxiv_id: '2611.02574'
url: https://arxiv.org/abs/2611.02574
methods:
- method:cispo
cites:
- paper:minimax-m1
tags:
- rlvr
- gotcha
---

# RLVR Sharpens the Pencil, Not the Mind

## Abstract Summary
OLMo-2-1B tracked across 13 GSM8K RLVR checkpoints: pass@1 58.0 to 61.3 but pass@256 coverage 94.5 to 96.9. Mistake probes stay AUROC 0.798-0.840 across checkpoints and error types. The only strong internal shift is at the final-answer token (AUROC 0.93); reasoning-step probes sit near chance.

## Key Contributions
1. Checkpoint-level evidence that this RLVR run reorders existing solution paths rather than sharpening internal error detection.

## Empirical Highlights
Gotcha on task:math-code-rl-dense. Complements paper:what-rl-brings / paper:outcome-rl-buys. Does not retarget CISPO.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.02574`
- Code: none found (`code_status: none`).
