---
id: paper:opd-grpo-flops
type: paper
title: 'Unpacking the Compute Efficiency of Strong-to-Weak OPD against GRPO'
authors:
- Zeyu Leo Liu
- Yang Li
- Bo Pang
- Emre Can Acikgoz
- Xuan-Phi Nguyen
- Anurag Koul
- Srijan Bansal
- Erik Nijkamp
- Shafiq Joty
- Semih Yavuz
year: 2026
month: 11
arxiv_id: '2611.08453'
url: https://arxiv.org/abs/2611.08453
methods:
- method:opd
- method:open-mopd
cites:
- paper:opd
- paper:open-mopd
- paper:opd-then-rlvr
- paper:opd-ood-consolidation
tags:
- distillation
- opd
- flops
- gotcha
---

# Unpacking the Compute Efficiency of Strong-to-Weak OPD against GRPO

## Abstract Summary
Matched-FLOPs comparison of reverse-KL OPD vs GRPO. With an external post-trained teacher, OPD generally loses accuracy per training FLOP and inflates length. When the teacher is the student's own GRPO checkpoint, OPD recovers that checkpoint's math accuracy with $50\times$ fewer distillation FLOPs than GRPO needs to reach it. Multi-teacher OPD consolidates per-domain GRPO specialists at $5.2\%$ (2 domains) / $8.0\%$ (4 domains) extra FLOPs; the 2-domain pipeline beats joint GRPO by $42.0\%$ fewer total FLOPs. Complements `paper:opd-then-rlvr`, `paper:rethink-mopd`, `paper:opd-ood-consolidation`.

## Key Contributions
1. External-teacher reverse-KL OPD is not cheaper than GRPO on held-out accuracy vs training FLOPs.
2. Self-GRPO teacher is the efficient distill setting ($50\times$ math; $6\times$ at 8 rollouts/prompt).
3. Specialist GRPO then MOPD is the compute-efficient multi-domain path vs joint GRPO.

## Empirical Highlights
Gotcha / recipe note on `task:student-distillation`. Distillation-stage $50\times$ does not count the cost of training the GRPO teacher; on a single domain that teacher is already the desired model. Does not retarget OPD or Open-MOPD.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.08453`
- Code: none found (`code_status: none`).
