---
id: paper:flashmorph2
type: paper
title: On-Policy Morphing into Hybrid Attention Models
authors:
- Disen Lan
- Xuanda Wang
- Jianbin Zheng
- Huafeng Kuang
- Wei Tang
- Yu Cheng
year: 2026
month: 11
arxiv_id: '2611.24809'
url: https://arxiv.org/abs/2611.24809
methods:
- method:flashmorph2
cites: []
tags:
- hybrid-attention
- layer-selection
- on-policy
- post-training
- active
---

# On-Policy Morphing into Hybrid Attention Models

## Abstract Summary
FlashMorph2 converts a pretrained Transformer into a hybrid full+linear attention model by selecting which layers keep full attention under a budget. It samples discrete hybrid architectures end to end (own hidden states) and jointly trains layer-selection scores with recovery weights, closing FlashMorph's off-policy mismatches. Vs FlashMorph: RULER +2.42 (63.26→65.68), LongBench +1.08 (29.86→30.94), recall +0.76. Layer selection 0.72–3.57 GPU-h for 0.6B–8B; 8.4–20.8× vs HALO, 560–854× vs KL-LS. Tight 6:1 GLA/GDN RULER 60.12 / 64.45 vs Uniform +10.65 / +7.86. No public v2 repo (`code_status: none`; v1 is LanDisen/FlashMorph). Does not retarget SAS or Mamba-2.

## Key Contributions
1. On-policy discrete hybrid forwards instead of continuous teacher-forced gates.
2. Joint layer-score and weight adaptation under the recovery objective.
3. Qwen3 0.6B–8B / 30B-A3B with GLA, GDN, Lightning Attention.

## Empirical Highlights
RULER 63.26→65.68; LongBench 29.86→30.94; 0.72–3.57 GPU-h selection. Ablation: drop on-policy computation −29.55 RULER.

## Open Source Repository & Resources
- Paper: `https://arxiv.org/abs/2611.24809`
- Code: `none found` (`code_status: none`; FlashMorph v1 is LanDisen/FlashMorph).
