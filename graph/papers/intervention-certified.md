---
id: paper:intervention-certified
type: paper
title: 'Intervention-Certified Amplification: A Validity Gate for sigma-Weighted Post-Training'
authors:
- 'Leiyue Chen'
- 'Meng Wei'
- 'Xuefeng Hu'
- 'Wei Liu'
year: 2026
month: 10
arxiv_id: '2610.33882'
url: https://arxiv.org/abs/2610.33882
methods:
- method:cispo
- method:olmo-3
cites:
- paper:minimax-m1
- paper:olmo-3
tags:
- rlvr
- gotcha
- sft
---

# Intervention-Certified Amplification: A Validity Gate for sigma-Weighted Post-Training

## Abstract Summary
Hybrid SFT/RL that sets per-sample balance from train-side signals can amplify pretrained behavior even after its literal form is removed. DIAA emits unexecuted TIR on 29% of MATH-500, 3x vanilla GRPO, after Python fences are stripped from the anchor.

## Key Contributions
1. Validity gate for sigma-weighted SFT/RL hybrids; not a CISPO replacement. EMNLP 2026 Findings.

## Empirical Highlights
Paired interventions: 10.6 pp accuracy recovery when TIR is suppressed. A student trained on a 0%-TIR teacher still inherits the pattern. Does not retarget CISPO or OLMo-3.
Venue: EMNLP 2026 Findings. Claim evidence_level remains preprint on attached methods; this is a gotcha note.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2610.33882`
- Code: `none found (`code_status: none`). Anthology: https://aclanthology.org/2026.findings-emnlp.2090/`
